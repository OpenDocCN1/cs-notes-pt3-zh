

## 回顾：同步元数据更新？

Xv6-rev0 策略：谨慎安排磁盘写入顺序以避免悬空引用

+   1. 在创建目录项之前先初始化新的 inode
+   2. 在标记 inode 为空闲之前先删除目录项
+   3. 在将块添加到 inode addrs[] 之前先标记块为已使用
+   4. 在标记为自由之前先从 addrs[] 中移除块
+   5. 在标记为自由之前先将块清零

存在一些可见的 bug：

. 和 .. 在 mkdir() 期间，链接计数，大小

存在一些不可见的遗留问题

可能丢失已释放的块和 inode

## 日志记录（Journaling）

### 目标：

- 相对于崩溃，系统调用是原子的
- 快速恢复（无需数小时的 fsck）
- 正常操作下具有写回缓存的速度

### 方法

将分两步引入日志记录

- 首先是 xv6 的 log，仅提供安全性
- 然后是 Linux EXT3，它也很快

## 日志记录背后的基本思想

为了确保原子性：

+   系统调用的所有写入都执行，或都不执行
+   我们将一个原子操作称为“事务”
+   记录系统调用*将要*执行的全部写入到日志中
+   然后记录“完成”
+   然后执行写入
+   在崩溃+恢复时：
+   如果日志中有“完成”，则重放日志中的所有写入
+   如果没有“完成”，则忽略日志
+   这是一个预写日志

## Xv6 的简单日志记录

FS 在磁盘上有一个日志 syscall：

- begin_trans()
- bp = bread()
- bp->data[] = ...
- log_write(bp)
- 更多写入 ...
- commit_trans()

![](img/53ee1e3b0eba43505c7d530851f32f6f_710_0.png)

## 回顾：balloc

```
// Allocate a zeroed disk block.
static uint
balloc(uint dev)
{
  int b, bi, m;
  struct buf *bp;
  struct superblock sb;

  bp = 0;
  readsb(dev, &sb);
  for(b = 0; b < sb.size; b += BPB){
    bp = bread(dev, BBLOCK(b, sb.ninodes));
    for(bi = 0; bi < BPB && b + bi < sb.size; bi++){
      m = 1 << (bi % 8);
      if((bp->data[bi/8] & m) == 0){
        bp->data[bi/8] |= m;
        log_write(bp);
        brelse(bp);
        bzero(dev + b + bi);
        return b + bi;
      }
    }
    brelse(bp);
  }
  panic("balloc: out of blocks");
}
```

![](img/53ee1e3b0eba43505c7d530851f32f6f_711_0.png)

```
void
log_write(struct buf *b)
{
    int i;

    if (log.lh.n >= LOGSIZE || log.lh.n >= log.size - 1)
        panic("too big a transaction");
    if (!log.busy)
        panic("write outside of trans");

    for (i = 0; i < log.lh.n; i++) {
        if (log.lh.sector[i] == b->sector)    // log absorbtion?
            break;
    }
    log.lh.sector[i] = b->sector;
    struct buf *lbuf = bread(b->dev, log.start+i+1);
    memmove(lbuf->data, b->data, BSIZE);
    bwrite(lbuf);
    brelse(lbuf);
    if (i == log.lh.n)
        log.lh.n++;
    b->flags |= B_DIRTY; // XXX prevent eviction
}
```

## Xv6 中的事务语义

begin_trans:
  需要指示哪些写入组必须原子！
  锁定 -- xv6 一次只允许一个事务
log_write:
  记录扇区 #
  将缓冲区内容追加到日志
  保留修改后的块在缓冲区缓存中（但不写入）
commit_trans():
  在日志中记录“完成”和扇区 #s
  执行写入
  从日志中擦除“完成”
recovery:
  如果日志显示“完成”：将块从日志复制到磁盘上的真实位置

```
void
begin_trans(void)
{
    acquire(&log.lock);
    while (log.busy) {
        sleep(&log, &log.lock);
    }
    log.busy = 1;
    release(&log.lock);
}

void
commit_trans(void)
{
    if (log.lh.n > 0) {
        write_head();       // Write header to disk -- the real commit
        install_trans();    // Now install writes to home locations
        log.lh.n = 0;
        write_head();       // Erase the transaction from the log
    }
    acquire(&log.lock);
    log.busy = 0;
    wakeup(&log);
    release(&log.lock);
}
```

## Sys_unlink

struct inode *dp =
nameiparent(path, name)

```
begin_trans();
ilock(dp);
// Cannot unlink "." or ".."
if(namecmp(name, ".") == 0 || namecmp(name, "..") == 0)
    goto bad;
if((ip = dirlookup(dp, name, &off)) == 0)
    goto bad;
ilock(ip);
if(ip->nlink < 1)
    panic("unlink: nlink < 1");
if(ip->type == T_DIR && !isdirempty(ip)){
    iunlockput(ip);
    goto bad;
}
memset(&de, 0, sizeof(de));
if(writei(dp, (char*)&de, off, sizeof(de)) != sizeof(de))
    panic("unlink: writei");
if(ip->type == T_DIR){
    dp->nlink--;
    iupdate(dp);
}
iunlockput(dp);
ip->nlink--;
iupdate(ip);
iunlockput(ip);
commit_trans();
```

