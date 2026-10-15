
## Review: Process in xv6 (proc.c)

```
54 // Per-process state
55 struct proc {
56   uint sz;                  // Size of process memory (bytes)
57   pde_t* pgdir;             // Page table
58   char *kstack;             // Bottom of kernel stack for this process
59   enum procstate state;     // Process state
60   volatile int pid;         // Process ID
61   struct proc *parent;      // Parent process
62   struct trapframe *tf;     // Trap frame for current syscall
63   struct context *context;  // swtch() here to run process
64   void *chan;               // If non-zero, sleeping on chan
65   int killed;               // If non-zero, have been killed
66   struct file *ofile[NOFILE]; // Open files
67   struct inode *cwd;        // Current directory
68   char name[16];            // Process name (debugging)
69 };
```

## Review: Context Switch in xv6

```
5 # Save current register context in old
6 # and then load register context from new.
7
8 .globl swtch          # Context switch
9 swtch:                #
10     movl 4(%esp), %eax   # void swtch(struct context **old, struct context *new);
11     movl 8(%esp), %edx   #
12
13 # Save old callee-save registers
14 pushl %ebp
15 pushl %ebx
16 pushl %esi
17 pushl %edi
18
19 # Switch stacks
20 movl %esp, (%eax)
21 movl %edx, %esp
22
23 # Load new callee-save registers
24 popl %edi
25 popl %esi
26 popl %ebx
27 popl %ebp
28 ret
```

```
# Context switch
#
# void swtch(struct context **old, struct context *new);
```

![](img/53ee1e3b0eba43505c7d530851f32f6f_327_0.png)

![](img/53ee1e3b0eba43505c7d530851f32f6f_327_1.png)

## Review: Context Switch in xv6

```
258 scheduler(void)
259 {
260   struct proc *p;
261 
262   for(;;){
263     // Enable interrupts on this processor.
264     sti();
265 
266     // Loop over process table looking for process to run.
267     acquire(&ptable.lock);
268     for(p = ptable.proc; p < &ptable.proc[NPROC]; p++){
269       if(p->state != RUNNABLE)
270         continue;
271 
272       // Switch to chosen process. It is the process's job
273       // to release ptable.lock and then reacquire it
274       // before jumping back to us.
275       proc = p;
276       switchuvm(p);
277       p->state = RUNNING;
278       swtch(&cpu->scheduler, proc->context);
279       switchkvm();
280 
281       // Process is done running for now.
282       // It should have changed its p->state before coming back.
283       proc = 0;
284     }
285     release(&ptable.lock);
286   }
287 }
```

```
290 // Enter scheduler. Must hold only ptable.lock
291 // and have changed proc->state.
292 void
293 sched(void)
294 {
295   int intena;
296 
297   if(!holding(&ptable.lock))
298     panic("sched ptable.lock");
299   if(cpu->ncli != 1)
300     panic("sched locks");
301   if(proc->state == RUNNING)
302     panic("sched running");
303   if(readeflags()&FL_IF)
304     panic("sched interruptible");
305   intena = cpu->intena;
306   swtch(&proc->context, cpu->scheduler);
307   cpu->intena = intena;
308 }
```

## Cooperating Processes

- **Independent** process cannot affect or be affected by the execution of another process
- **Cooperating** process can affect or be affected by the execution of another process
- Advantages of process cooperation
  - Information sharing
  - Computation speed-up
  - Modularity
  - Convenience

## Communications Models

![](img/53ee1e3b0eba43505c7d530851f32f6f_330_0.png)

## IPC

- Cooperating processes need **inter-process communication (IPC)**
- Two models of IPC
  - Shared memory
  - Message passing
- In POSIX
  - Pipe, msg passing, signal, shared memory, semaphore, etc.

## Examples of IPC Systems - POSIX

- POSIX Shared Memory
  - Process first creates shared memory segment
    `segment_id = shmget(IPC_PRIVATE, size, S_IRUSR | S_IWUSR);`
  - Process wanting access to that shared memory must attach to it
    `shared_memory = (char *) shmat(id, NULL, 0);`
  - Now the process could write to the shared memory
    `sprintf(shared_memory, "Writing to shared memory");`
  - When done a process can detach the shared memory from its address space
    `shmdt(shared_memory);`
