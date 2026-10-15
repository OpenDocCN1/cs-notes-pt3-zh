
## The most surprising error

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

- T1 enters FindHandle with scsiLock, calls Validate, calls CpuSched_Wait (rel scsiLock, sleep w/ handleArrayLock)
- T2 acquires scsiLock and calls FindHandle. Boom.

## Lock Analysis in Real World

- Lockdep analysis
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

## Valgrind: a useful tool for program debugging/analysis

## What is Valgrind

- Linux, x86, program analyzer
- Advantages
    - powerful
    - no recompiles, just binaries
    - any language (!)
    - extensible, configurable
    - free, GPL'd goodness
- Speed slowdown

![](img/53ee1e3b0eba43505c7d530851f32f6f_962_0.png)

## What are the existing skins

- MemCheck
    - Heavy duty memory checker
- AddrCheck
    - Faster, cheaper
- Cachegrind
    - Caching info
- Helgrind
    - Thread semantics
- Others

![](img/53ee1e3b0eba43505c7d530851f32f6f_963_0.png)

![](img/53ee1e3b0eba43505c7d530851f32f6f_963_1.png)

## Other features

![](img/53ee1e3b0eba43505c7d530851f32f6f_964_0.png)

- Callgraphs
- Multiple other patches
    - Open file descriptors
- Suppressions
    - Selective understanding
- Ignore System libs
    - Yes, bugs
- /dev/random

## How to Use it

- apt-get install valgrind

You invoke Valgrind like this:

```
valgrind [valgrind-options] your-prog [your-prog-options]
```

The most important option is --tool which dictates which Valgrind tool to run.

```
valgrind --tool=memcheck ls -l
```

## Example code

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

## How Valgrind Detect it

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

## MANY OTHER USEFUL FEATURES
