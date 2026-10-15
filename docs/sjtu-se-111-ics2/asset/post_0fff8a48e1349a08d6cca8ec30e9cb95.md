
## Nonlocal Jumps

```
#include <setjmp.h>

int setjmp(jmp_buf env);

Returns: 0 from setjmp, nonzero from long jumps

#include <setjmp.h>
void longjmp(jmp_buf env, int retval);

Never returns
```

```
1 #include "csapp.h"
2
3 jmp_buf buf;
4
5 int error1 = 0;
6 int error2 = 1;
7
8 void foo(void), bar(void);
9
10 int main()
11 {
12     int rc;
13
14     rc = setjmp(buf);
15     if (rc == 0)
16         foo();
17     else if (rc == 1)
18         printf("Detected an error1 condition in foo\n");
19     else if (rc == 2)
20         printf("Detected an error2 condition in foo\n");
21     else
22         printf("Unknown error condition in foo\n");
23     exit(0);
24 }
```

```
25
26 /* deeply nested function foo */
27 void foo(void)
28 {
29     if (error1)
30         longjmp(buf, 1);
31     bar();
32 }
33
34 void bar(void)
35 {
36     if (error2)
37         longjmp(buf, 2);
38 }
```

## Nonlocal Jumps

```
#include <setjmp.h>

int sigsetjmp(sigjmp_buf env, int savesigs);
Returns: 0 from sigsetjmp, nonzero from siglongjumps

#include <setjmp.h>
void siglongjmp(sigjmp_buf env, int retval);
Never returns
```

```c
#include "csapp.h"
sigjmp_buf buf;

void handler(int sig) { siglongjmp(buf, 1); }

int main()
{
    Signal(SIGINT, handler);

    if (!sigsetjmp(buf, 1))
        printf("starting\n");
    else
        printf("restarting\n");

    while(1) {
        sleep(1);
        printf("processing...\n");
    }
    exit(0);
}
```

## System-Level I/O

## Outline

- Unix I/O
- Reading File Metadata
- Sharing Files & I/O redirection
- Robust I/O
- Standard I/O
- Suggested Reading
  - 10.1~10.3, 10.5~10.7, 10.4, 10.8

## Why Unix I/O

- Input/Output
  - A process of copying data between main memory and external devices
- Standard I/O library
  - User level or high level I/O functions

## Why Unix I/O

- Unix I/O
  - I/O functions provided by kernel
  - Helps you understand other system concepts
    - I/O vs. process
  - Sometimes, it is the only choice

## Unix I/O

- A Unix file is a sequence of m bytes
  - B₀, B₁, ......, Bₖ, ......, Bₘ
- All I/O devices are modeled as files
  - such as networks, disks, and terminals
  - allows Unix to export a simple, low-level application interface, known as Unix I/O,

## Unix I/O

- All input and output is performed by reading and writing the appropriate files
  - Enables all input and output to be performed in a uniform and consistent way.

## Open Files

- An application announces its intention to access an I/O device
  - The kernel opens the corresponding file
  - The kernel returns a small non-negative integer, descriptor
    - Identifies the file in all subsequent operations on the file
  - The kernel keeps track of all information about the open file
    - Maintains a file position k, initially 0, for each open file

## Kernel Data Structures for Files

![](img/9bd5f6161cb6607b56d2fb964d1b8794_608_0.png)

## Descriptor table

- Each process has it own separate descriptor table
  - whose entries are indexed by the process's open file descriptors
  - each open descriptor entry points to an entry in the file table

## File table

- The set of open files is represented by a file table
- File table is shared by all processes
- Each file table entry consists
  - the current file position
  - a reference count of the number of descriptor entries that currently point to it
  - a pointer to an entry in the v-node table
  - the kernel deletes a file table entry when its reference count becomes zero

## V-node table

- V-node table is shared by all processes
- Each entry contains most of the information
  of a file

## Kernel Data Structures for Files

![](img/9bd5f6161cb6607b56d2fb964d1b8794_612_0.png)
