

## 最令人惊讶的错误

```
// Entered holding scsiLock
int FindHandle(int handleID) {
    prevIRQL = SP_LockIRQ(&handleArrayLock, ...);
    Validate(handle);
    ...
int Validate(handle) {
    ASSERT(SP_IsLocked(&scsiLock));
    while (adapter->openInProgress) {
        CpuSched_Wait(&adapter->openInProgress,
            CPUSCHED_WAIT_SCSI, &scsiLock);
        SP_Lock(&scsiLock);
```

- T1 进入 FindHandle 并持有 scsiLock，调用 Validate，调用 CpuSched_Wait（释放 scsiLock，持有 handleArrayLock 时睡眠）
- T2 获取 scsiLock 并调用 FindHandle。爆炸。

## 实际世界中的锁分析

- Lockdep 分析
    - https://www.kernel.org/doc/Documentation/lockdep-design.txt

```
Chain exists of:
&of->mutex --> sr_mutex --> &mm->mmap_sem

Possible unsafe locking scenario:

        CPU0                  CPU1
        ----                  ----
lock(&mm->mmap_sem);

                        lock(sr_mutex);
                        lock(&mm->mmap_sem);

lock(&of->mutex);
*** DEADLOCK ***
```

```
======================================================
[ INFO: possible circular locking dependency detected ]
3.12.0+ #2 Not tainted
------------------------------------------------------

trinity-child0/9004 is trying to acquire lock:
(&of->mutex){+.+.+}, at: [<ffffffff8123c0cf>] sysfs_bin_mmap+0x4f/0x120

but already holding lock:
(&mm->mmap_sem){++++++}, at: [<ffffffff8116b5ff>] vm_mmap_pgoff+0x6f/0xc0
which lock already depends on the new lock.
```

## Valgrind：程序调试/分析的有用工具

## 什么是 Valgrind

- Linux, x86, 程序分析器
- 优点
    - 功能强大
    - 无需重新编译，只需二进制文件
    - 任何语言（！）
    - 可扩展，可配置
    - 免费，GPL 许可的优秀工具
- 速度变慢

![](img/53ee1e3b0eba43505c7d530851f32f6f_962_0.png)

## 现有的皮肤有哪些

- MemCheck
    - 重型内存检查器
- AddrCheck
    - 更快，更便宜
- Cachegrind
    - 缓存信息
- Helgrind
    - 线程语义
- 其他

![](img/53ee1e3b0eba43505c7d530851f32f6f_963_0.png)

![](img/53ee1e3b0eba43505c7d530851f32f6f_963_1.png)

## 其他功能

![](img/53ee1e3b0eba43505c7d530851f32f6f_964_0.png)

- 调用图
- 多个其他补丁
    - 打开的文件描述符
- 抑制
    - 选择性理解
- 忽略系统库
    - 是的，有 bug
- /dev/random

## 如何使用它

- apt-get install valgrind

你这样调用 Valgrind：

```
valgrind [valgrind-options] your-prog [your-prog-options]
```

最重要的选项是 --tool，它决定运行哪个 Valgrind 工具。

```
valgrind --tool=memcheck ls -l
```

## 示例代码

```
int main ( void )
{
    int r;
    pthread_mutex_t mx1, mx2;
    r = pthread_mutex_init( &mx1, NULL ); assert(r==0);
    r = pthread_mutex_init( &mx2, NULL ); assert(r==0);

    r = pthread_mutex_lock( &mx1 ); assert(r==0);
    r = pthread_mutex_lock( &mx2 ); assert(r==0);

    r = pthread_mutex_unlock( &mx1 ); assert(r==0);
    r = pthread_mutex_unlock( &mx2 ); assert(r==0);

    r = pthread_mutex_lock( &mx2 ); assert(r==0); /* error */
    r = pthread_mutex_lock( &mx1 ); assert(r==0);

    r = pthread_mutex_unlock( &mx1 ); assert(r==0);
    r = pthread_mutex_unlock( &mx2 ); assert(r==0);

    r = pthread_mutex_destroy( &mx1 );
    r = pthread_mutex_destroy( &mx2 );

    return 0;
}
```

## Valgrind 如何检测它

```
Thread #1: lock order "0x7FEFFFAB0 before 0x7FEFFFA80" violated
    at 0x4C23C91: pthread_mutex_lock (hg_intercepts.c:388)
    by 0x40081F: main (tc13_laog1.c:24)
Required order was established by acquisition of lock at 0x7FEFFFAB0
    at 0x4C23C91: pthread_mutex_lock (hg_intercepts.c:388)
    by 0x400748: main (tc13_laog1.c:17)
followed by a later acquisition of lock at 0x7FEFFFA80
    at 0x4C23C91: pthread_mutex_lock (hg_intercepts.c:388)
    by 0x400773: main (tc13_laog1.c:18)
```

## 还有许多其他有用的功能

