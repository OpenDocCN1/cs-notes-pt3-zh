
## System Call Implementation

### Application Programming Interface (API)

- API functions invoke the actual system calls on behalf of the application programmer
- Just needs to obey API and understand what OS will do as a result call, most details of OS interface hidden from programmer by API
- APIs are Managed by **run-time support library** (set of functions built into libraries included with compiler)

- Discuss: Why do users use APIs rather than system calls?

- **Three most common APIs**
  - **Win32 API** for Windows
  - **POSIX API** for POSIX-based systems (including virtually all versions of UNIX, Linux, and Mac OS X)
  - **Java API** for the Java virtual machine (JVM)

### Relationship between API, SCI, OS

![](img/0f9477f9dd9e571abf0b2ce4550a9e88_95_0.png)

### Standard C Library Example

C program invoking printf() library call, which calls write() system call

```c
#include <stdio.h>
int main ()
{
...
printf("Greetings");
...
return 0;
}
```

![](img/0f9477f9dd9e571abf0b2ce4550a9e88_96_0.png)

### System Call Parameter Passing

- Often, more information is required than simply identity of desired system call
- Three general methods used to pass parameters to the OS
  - Simplest: pass the parameters in *registers*
  - Parameters stored in a *block*, or table, in *memory*, and *address* of block passed as a parameter in a *register*
  - Parameters placed, or *pushed*, onto the *stack* by the *program* and *popped* off the stack by the operating system

**Parameter Passing via Table**

![](img/0f9477f9dd9e571abf0b2ce4550a9e88_98_0.png)

### Types of System Calls

- Process control
- File management
- Device management
- Information maintenance
- Communications

- **Process control**
  - end, abort
  - load, execute
  - create and terminate process
  - get and set process attributes
  - wait for time
  - wait event, signal event
  - allocate and free memory

- **Information maintenance**
  - get and set time or date
  - get and set system data
  - get and set process, file or device attributes

- **Communications**
  - create and delete communication connection
  - send and receive message
  - transfer status information
  - attach or detach remote devices

### Communication Models

- Communication may take place using either **message passing** or **shared memory**.

![](img/0f9477f9dd9e571abf0b2ce4550a9e88_103_0.png)

### Outline

- Operating System Functions
- Operating System Services
- Operating System Interfaces
- Operating System Structure
- Operating System Design and Implementation

### Operating System Structure

- Simple Structure
- Layered Structure
  - Virtual Machines
- Microkernel Structure
- Modules

### Simple Structure

- **MS-DOS**
  - Written to provide the most functionality in the least space
  - Not divided into modules
  - Although MS-DOS has some structure, its interfaces and levels of functionality are not well separated

- **Original UNIX**
  - Two separable parts
    - Systems programs
    - **The kernel**: Consists of everything below the system-call interface and above the physical hardware, provides a large number of functions for one level

### UNIX System Structure

```
(the users)

shells and commands
compilers and interpreters
system libraries

system-call interface to the kernel

Kernel

signals terminal handling
character I/O system
terminal drivers

file system
swapping block I/O system
disk and tape drivers

CPU scheduling
page replacement
demand paging
virtual memory

kernel interface to the hardware

terminal controllers
terminals

device controllers
disks and tapes

memory controllers
physical memory
```
