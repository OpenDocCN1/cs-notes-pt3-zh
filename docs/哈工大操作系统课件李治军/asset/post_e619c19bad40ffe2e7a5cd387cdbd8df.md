
# 引入目录树

+   将划分后的集合再进行划分：k次划分后，每个集合中的文件数为O(logₖN)

这一树状结构扩展性好、表示清晰，最常用

引入了一个新的东西：目录，表示一个文件集合

![](img/365fc74cce32b405409a65a7e8830bec_360_0.png)

# 树状目录的完整实现

磁盘

FCB数组

数据盘块集合

"/"的FCB

"/"的数据块

目录项：文件名+对应的FCB的“地址”！

<var, 13> <my, 82>

"my"的FCB

"my"的数据块

<data, 103> <cont, 225> <mail, 77>

var my

cat bo hex

data cont mail

a data

# 要使整个系统能自举，还需存一些信息

FCB数组

数据盘块集合

引导块 超级块 i节点位图 盘块位图 i节点 数据区

-   inode位图: 哪些inode空闲，哪些被占用
-   盘块位图: 哪些盘块是空闲的，硬盘大小不同这个位图的大小也不同
-   空闲位图(位向量)... 0011110011101 表示磁盘块2、3、4、5、8、9、10、12空闲
-   超级块: 记录两个位图有多大等信息

# “完成全部映射下” 的磁盘使用

用户
读test.c 202-212个字节

open(/xx/test.c)
目录解析找到/, 读入/内容找到xx, 再找到test.c的inode

read(fd)
根据找到的FCB和file中的202-212字节找磁盘块789

写入电梯队列
add_request(789)

磁盘中断
从队列中取出789, 算出 cyl,head,sector

写磁盘控制器
outp(cyl,head,sector)

inode数组 数据盘块

![](img/365fc74cce32b405409a65a7e8830bec_364_0.png)

![](img/365fc74cce32b405409a65a7e8830bec_364_1.png)

# 操作系统

# Operating Systems

# L32 目录解析代码实现

# Directory Resolution

lizhijun_os@hit.edu.cn

授课教师：李治军

综合楼411室

# “完成全部映射下”的磁盘使用

-   用户
-   read test.c 202-212个字节
-   open(/xx/test.c)
-   目录解析找到/，读入/内容找到xx，再找到test.c的inode
-   read(fd)
-   根据找到的FCB和file中的 202-212字节找盘块789
-   写入电梯队列
-   add_request(789)
-   磁盘中断
-   从队列中取出789，算出 cyl,head,sector
-   写磁盘控制器
-   outp(cyl,head,sector)

![](img/365fc74cce32b405409a65a7e8830bec_366_0.png)

![](img/365fc74cce32b405409a65a7e8830bec_366_1.png)

![](img/365fc74cce32b405409a65a7e8830bec_366_2.png)

# 一个实际运转的文件系统!

![](img/365fc74cce32b405409a65a7e8830bec_367_0.png)

# 就是将open弄明白...

```
在linux/fs/open.c中
int sys_open(const char* filename, int flag)
{ i=open_namei(filename,flag,&inode); 解析路径! ... }
```

```
int open_namei(...)
{ dir=dir_namei(pathname,&namelen,&basename); }
```

```
static struct m_inode *dir_namei()
{ dir=get_dir(pathname); }
```

解析路径!

![](img/365fc74cce32b405409a65a7e8830bec_368_0.png)

# get_dir完成真正的目录解析

```
static struct m_inode *get_dir(const char *pathname)
{ if((c=get_fs_byte(pathname))=='/')
    {inode=current->root; pathname++;}
else if(c) inode=current->pwd;
while(1){if(!c) return inode; //函数的正确出口
bh=find_entry(&inode,thisname,namelen,&de);
int inr=de->inode; int idev=inode->i_dev;
inode=iget(idev,inr); //根据目录项读取下一层inode}}
```

解析从此处开始！

-   ■ 核心的四句话正好对应目录树的四个
-   重点：(1)root: 找到根目录；
-   (2)find_entry: 从目录中读取目录项；
-   (3)inr: 是目录项中的索引节点号；
-   (4)iget: 再读下一层目录

![](img/365fc74cce32b405409a65a7e8830bec_369_0.png)

# 目录解析 — 从根目录开始

```
inode=current->root;
```

又是current(task_struct)，仍然是拷贝自init进程

```
void init(void)
{  setup((void *) &drive_info), ... }
```

一句看过无数次，又略过无数次的语句

```
sys_setup(void * BIOS)//在kernel/hd.c中
{ hd_info[drive].head = *(2+BIOS);
  hd_info[drive].sect = *(14+BIOS);
  mount_root(); ... }
```

```
void mount_root(void)//在fs/super.c中
{
  mi=iget(ROOT_DEV,ROOT_INO));
  current->root = mi;
}
```

```
#define ROOT_INO 1
```

![](img/365fc74cce32b405409a65a7e8830bec_370_0.png)

# 读取inode — iget

```
struct m_inode * iget(int dev, int nr)
{ struct m_inode *inode = get_empty_inode();
inode->i_dev=dev; inode->i_num=nr;
read_inode(inode); return inode;}
```

```
static void read_inode(struct m_inode *inode)
{ struct super_block *sb=get_super(inode->i_dev);;
lock_inode(inode);
block=2+sb->s_imap_blocks+sb->s_zmap_blocks+
(inode->i_num-1)/INODES_PER_BLOCK;
bh=bread(inode->i_dev,block);
inode=bh->data[(inode->i_num-1)%INODES_PER_BLOCK];
unlock_inode(inode); }
```

引导块 超级块

i节点位图 盘块位图

i节点

数据区

# 开始目录解析 — find_entry(&inode,name,...,&de)

de: directory entry(目录项)

```
struct dir_entry{
  unsigned short inode; //i节点号
  char name[NAME_LEN]; //文件名 }
```

```
#define NAME_LEN 14
```

```
在fs/namei.c中
static struct buffer_head *find_entry(struct m_inode **dir, char *name, ..., struct dir_entry ** res_dir)
{ int entries=(*dir)->i_size/(sizeof(struct dir_entry));
int block=(*dir)->i_zone[0];
*bh=bread((*dir)->i_dev, block);
struct dir_entry *de =bh->b_data;
while(i<entries) {
  if(match(namelen,name,de))
  {*res_dir=de; return bh;}de++; i++;} }
```

![](img/365fc74cce32b405409a65a7e8830bec_372_0.png)
