
## Many-to-One Model

![](img/9321d6c42b8369e67ceb1f1d7e27b09c_263_0.png)

user thread

kernel thread

## Supplement: ULT States vs. Process States

![](img/9321d6c42b8369e67ceb1f1d7e27b09c_264_0.png)

thread1

thread2

Process A

Issue an I/O request, Process A is blocked.

Time out

Thread 2 need to coordinate With Thread 1

## One-to-One Model

- Each user-level thread maps to a kernel thread.
- Allows another thread to run when a thread makes a blocking system call.
- Allows multiple threads to run in parallel on multiprocessors.
- Creating a user thread requires creating the corresponding kernel thread.
- Restrict the number of threads supported by the system.
- Examples of systems using this model
  - Windows NT/XP/2000
  - Linux
  - Solaris 9 and later

## One-to-one Model

![](img/9321d6c42b8369e67ceb1f1d7e27b09c_266_0.png)

user thread

kernel thread

## Many-to-Many Model

- Allows many user level threads to be mapped to many kernel threads.
- Allows the operating system to create a sufficient number of kernel threads.
- When a thread performs a blocking system call, the kernel can schedule another thread for execution.
- Examples of systems supporting this model
  - Solaris prior to version 9
  - Windows NT/2000 with the *ThreadFiber* package

## Many-to-Many Model

![](img/9321d6c42b8369e67ceb1f1d7e27b09c_268_0.png)

user thread

kernel thread

## Two-level Model

- Similar to M:M, except that it allows a user thread to be bound to a kernel thread
- Examples of systems supporting this model
  - IRIX
  - HP-UX
  - Tru64 UNIX
  - Solaris 8 and earlier

## Comparison of these three models

- Many-to-one model allows the developer to create as many user threads as he wishes, true concurrency is not gained because the kernel can schedule only one thread at a time.
- One-to-one model allows for greater concurrency, but the developer has to be careful not to create too many threads within an application.
- Many-to-many model allows the developer to create as many user threads as necessary, and the corresponding kernel threads can run in parallel on a multiprocessor.

## 4.3 Thread Libraries

- Provides the programmer an API for creating and managing threads
- Two implementing ways
  - Provides a library entirely in user space with no kernel support. (-- local function call)
    code and data structures exist in user space
  - Implement a kernel-level library supported directly by the OS. (-- system call)
    code and data structures exist in kernel space
- Main thread library
  - POSIX Pthreads
  - Win32
  - java

## POSIX Pthreads

- **POSIX:**
  Portable Operating System Interface for computer environment
- a POSIX standard (IEEE 1003.1c) defining an API for thread creation and synchronization.
- API specifies behavior of the thread library, implementation is up to development of the library.
- Common in UNIX and Linux operating systems.
- Referred to user-level library, because no distinct relationship exists between a thread created using the Pthread API and any associated kernel threads.

## Multithreaded C program using the Pthreads API

```
```c
#include <pthread.h>
#include <stdio.h>

int sum;  /* this data is shared by the thread(s) */
void *runner(void *param);      /* the thread */

int main(int argc, char *argv[])
{
    pthread_t tid;          /* the thread identifier */
    pthread_attr_t attr;    /* set of attributes for the thread */

    if (argc != 2) {
        fprintf(stderr, "usage: a.out <integer value>\\n");
        return -1;
    }
    if (atoi(argv[1]) < 0) {
        fprintf(stderr, "Argument %d must be non-negative\\n", atoi(argv[1]));
        return -1;
    }
```

```
