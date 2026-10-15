
## Indirect Communication

- Mailbox sharing
  - $P_1$, $P_2$, and $P_3$ share mailbox A
  - $P_1$, sends; $P_2$ and $P_3$ receive
  - Who gets the message?
- Solutions
  - Allow a link to be associated with at most two processes
  - Allow only one process at a time to execute a receive operation
  - Allow the system to select arbitrarily the receiver. Sender is notified who the receiver was.

## Synchronization & Asynchronous

- Message passing may be either blocking or non-blocking
- **Blocking** is considered **synchronous**
  - **Blocking send** has the sender block until the message is received
  - **Blocking receive** has the receiver block until a message is available
- **Non-blocking** is considered **asynchronous**
  - **Non-blocking** send has the sender send the message and continue
  - **Non-blocking** receive has the receiver receive a valid message or null

## Buffering

- Queue of messages attached to the link; implemented in one of three ways
  1. Zero capacity – 0 messages
     Sender must wait for receiver (rendezvous)
  2. Bounded capacity – finite length of *n* messages
     Sender must wait if link full
  3. Unbounded capacity – infinite length
     Sender never waits

## Examples of IPC Systems - POSIX

- POSIX Shared Memory
  - Process first creates shared memory segment
    `segment id = shmget(IPC PRIVATE, size, S IRUSR | S IWUSR);`
  - Process wanting access to that shared memory must attach to it
    `shared memory = (char *) shmat(id, NULL, 0);`
  - Now the process could write to the shared memory
    `sprintf(shared memory, "Writing to shared memory");`
  - When done a process can detach the shared memory from its address space
    `shmdt(shared memory);`

## Examples of IPC Systems - WinXP (cont.)

- Communication works as follows:
  - The client opens a handle to the subsystem’s connection port object
  - The client sends a connection request
  - The server creates two private communication ports and returns the handle to one of them to the client
  - The client and server use the corresponding port handle to send messages or callbacks and to listen for replies

## Local Procedure Calls in Windows XP

![](img/53ee1e3b0eba43505c7d530851f32f6f_315_0.png)

## Communications in Client-Server Systems

- Sockets
- Remote Procedure Calls
- Remote Method Invocation (Java)

## INTERRUPT, TRAP, SYS CALL

## Requirements

- Must save the processor’s registers for future transparent resume
- Must be set up for execution in the kernel
- Must chose a place for the kernel to start executing
- Must be able to retrieve information about the event, e.g., system call arguments
- Must all be done securely
- Must maintain isolation of user processes and the kernel

## IDT

- IDT: interrupt descriptor table
  - Has 256 entries
  - Each giving the %cs and %eip to be used when handling the corresponding interrupt
- System call
  - A program invokes *int n*
  - *n* specifies the index into the IDT

## Kernel Stack

![](img/53ee1e3b0eba43505c7d530851f32f6f_322_0.png)

Figure 3-1. Kernel stack after an int instruction.

## tvinit

```
17 void
18 tvinit(void)
19 {
20     int i;
21
22     for(i = 0; i < 256; i++)
23         SETGATE(idt[i], 0, SEG_KCODE<<3, vectors[i], 0);
24         SETGATE(idt[T_SYSCALL], 1, SEG_KCODE<<3, vectors[T_SYSCALL], DPL_USER);
25
26         initlock(&tickslock, "time");
27 }
```

## IPC

Yubin Xia, Rong Chen
IPADS, SJTU

ACKs: Some slides are adapted from the textbook’s original slides and Frans’s OS course notes

## Review: Threads in xv6

```
// Saved registers for kernel context switches.
// Don't need to save all the segment registers (%cs, etc),
// because they are constant across kernel contexts.
// Don't need to save %eax, %ecx, %edx, because the
// x86 convention is that the caller has saved them.
// Contexts are stored at the bottom of the stack they
// describe; the stack pointer is the address of the context.
// The layout of the context matches the layout of the stack in swtch.S
// at the "Switch stacks" comment. Switch doesn't save eip explicitly,
// but it is on the stack and allocproc() manipulates it.
struct context {
  uint edi;
  uint esi;
  uint ebx;
  uint ebp;
  uint eip;
};
```
