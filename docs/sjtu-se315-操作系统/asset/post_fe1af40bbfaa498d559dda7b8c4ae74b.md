
## Null pointer fun

### Use-then-check

```c
/* 2.4.7: drivers/char/mxser.c */
struct mxser_struct *info = tty->driver_data;
unsigned flags;
if (!tty || !info->xmit_buf)
    return 0;
```

### Contradiction/redundant checks

```c
/* 2.4.7/drivers/video/tdfxfb.c */
fb_info.regbase_virt = ioremap_nocache(...);
if (!fb_info.regbase_virt)
    return -ENXIO;
fb_info.bufbase_virt = ioremap_nocache(...);

if (!fb_info.regbase_virt) {
    iounmap(fb_info.regbase_virt);
}
```

## Internal Consistency: finding security holes

Applications are bad:

- Rule: “do not dereference user pointer `p`”
- One violation = security hole
- Big Problem: which are the user pointers???

Sol’n: forall pointers, cross-check two OS beliefs

- “`*p`” implies safe kernel pointer
- “`copyin(p)/copyout(p)`” implies dangerous user pointer
- Error: pointer `p` has both beliefs.

## Statistical: Deriving deallocation routines

Use-after-free errors are horrible.

Problem: lots of undocumented sub-system free functions

Soln: derive behaviorally: pointer “p” not used after call “foo(p)” implies MAY belief that “foo” is a free function

Conceptually: Assume all functions free all arguments

(in reality: filter functions that have suggestive names)

## A bad free error

```c
/* drivers/block/cciss.c:cciss_ioctl */
if (iocommand.Direction == XFER_WRITE) {
    if (copy_to_user(...)) {
        cmd_free(NULL, c);
        if (buff != NULL) kfree(buff);
        return( -EFAULT);
    }
}
if (iocommand.Direction == XFER_READ) {
    if (copy_to_user(...)) {
        cmd_free(NULL, c);
        kfree(buff);
    }
}

cmd_free(NULL, c);
if (buff != NULL) kfree(buff);
```

## “A must be followed by B”

“a(); ... b();” implies MAY belief that a() follows b()

You might believe a-b paired, or might be a coincidence

## Checking derived lock functions

### Simplest

```c
/* fs/proc/inode.c:41:de_put: */
lock_kernel();
if (!de->count) {
    printk("de_put: entry already free!\n");
    return;
}
unlock_kernel();
```

### Evilest

```c
/* 2.4.1: drivers/sound/trident.c:trident_release: */
lock_kernel();
card = state->card;
dmabuf = &state->dmabuf;
VALIDATE_STATE(state);

#define VALIDATE_MAGIC(FOO,MAG)
({ \
    if (!(FOO) || (FOO)->magic != MAG) { \
        printk(invalid magic, __FUNCTION__); \
        return -ENXIO; \
    } \
})

#define VALIDATE_STATE(a) VALIDATE_MAGIC(a,TRIDENT_STATE_MAGIC)
```

## General Rules

- Do not call blocking functions with interrupts disabled or spin lock held
- check for NULL results
- Do not allocate large stack variables
- Do not re-use already-allocated memory
- Check user pointers before using them in kernel mode
- Release acquired locks

## Unstated Rules in JOS

- Interrupts are disabled in kernel mode
- Only env 1 has access to disk
- All registers are saved & restored on context switch
- Application code is never executed with CPL 0
- Don't allocate an already-allocated physical page
- Propagate error messages to user applications (e.g., out of resources)
- A spawned program should have open only file descriptors 0, 1, and 2.
- User pointers should be run through TRUP before used by the kernel

## Next Class

- Data Race
- Deadlock

## Data Race & DeadLock

Rong Chen

## Outline

- Happens-before Race Detection
- Lockset-Based Race Detection
- Deadlocks
- Detecting deadlocks using Lockset Analysis

## Data Race Detection

## What is Race?

![](img/53ee1e3b0eba43505c7d530851f32f6f_900_0.png)

## Data Race

An undesirable situation that occurs when a device or system attempts to perform two or more operations at the same time, but the operations must be done in the proper sequence in order to be done correctly

- multithread
- distributed Programs

### Key reason

- separate processes or threads of execution depends on same shared state

## Data Race

![](img/53ee1e3b0eba43505c7d530851f32f6f_902_0.png)
