
## Rescheduling Softirqs
- A softirq routine can reschedule itself
- This could starve user-level processes
- Softirq scheduler only runs a limited number of requests at a time
- The rest are executed by a kernel thread, `ksoftirqd`, which competes with user processes for CPU time

## Tasklets
- Built on top of softirqs
- Can be created and destroyed dynamically
- Run on the CPU that scheduled it (cache affinity)
- Individual tasklets are locked during execution; no problem about re-entrancy, and no need for locking by the code
- Tasklets can run in parallel on multiple CPUs
  - *Same* tasklet can only run on one CPU
- Were once the preferred mechanism for most deferred activity, now changing

## The Trouble with Tasklets
- Hard to get right
- One has to be careful about sleeping
- They run at higher priority than other tasks in the systems
- Can produce uncontrolled latency if coded badly
- Ongoing discussion about eliminating tasklets
- Will likely slowly fade over time

## Work Queues
- Always run by kernel threads
  - Are scheduled by the scheduler
- Softirqs and tasklets run in an interrupt context; work queues have a pseudo-process context
  - i.e., have a kernel context but no user context
- Because they have a pseudo-process context, they can sleep
  - Work queues are shared by multiple devices
  - Thus, sleeping will delay other work on the queue
- However, they are kernel-only; there is no user mode associated with it
  - Don’t try copying data into/out of user space

## Kernel Threads
- Always operate in kernel mode
  - Again, no user context
- 2.6.30 introduced the notion of *threaded interrupt handlers*
  - Imported from the realtime tree
  - `request_threaded_irq()`
  - Now each bottom half has its own context, unlike work queues
  - Idea is to eventually replace tasklets and work queues

## Comparing Approaches

| | ISR | SoftIRQ | Tasklet | WorkQueue | KThread |
|---|---|---|---|---|---|
| Will disable all interrupts? | Briefly | No | No | No | No |
| Will disable other instances of self? | Yes | Yes | No | No | No |
| Higher priority than regular scheduled tasks? | Yes | Yes* | Yes* | No | No |
| Will be run on same processor as ISR? | N/A | Yes | Yes | Yes | Maybe |
| More than one run can on same CPU? | No | No | No | Yes | Yes |
| Same one can run on multiple CPUs? | Yes | Yes | No | Yes | Yes |
| Full context switch? | No | No | No | Yes | Yes |
| Can sleep? (Has own kernel stack) | No | No | No | Yes | Yes |
| Can access user space? | No | No | No | No | No |

*Within limits, can be run by ksoftirqd

## I/O

Yubin Xia, Rong Chen
IPADS, SJTU

## Review
- Interrupt concepts
  - IDT, Trap Num, Interrupt vector, IRQ, System call number, …
  - Vectors usually IRQ# + 32
  - Triple fault
- Interrupt process
  - Device, PIC (8259A), IDT, trap()
  - CPU checks interrupt every cycle, if interrupt enabled
  - Masked interrupt, umaskable interrupt

## Intel-Reserved ID-Numbers
- Of the 256 possible interrupt ID numbers, Intel reserves the first 32 for ‘exceptions’
- OS’s such as Linux are free to use the remaining 224 available interrupt ID numbers for their own purposes (e.g., for service-requests from external devices, or for other purposes such as system-calls)
- Examples:
  - 0: divide-overflow fault
  - 6: Undefined Opcode
  - 7: Coprocessor Not Available
  - 11: Segment-Not-Present fault
  - 12: Stack fault
  - 13: General Protection Exception
  - 14: Page-Fault Exception

## Summary: Interrupts vs Exceptions
- Varying terminology but for Intel:
  - **Interrupt** (asynchronous, device generated)
    - Maskable: device-generated, associated with IRQs (interrupt request lines); may be temporarily disabled (still pending)
    - Nonmaskable: some critical hardware failures
  - **Exceptions** (synchronous, from software)
    - Processor-detected
      - Faults – correctable (restartable); e.g. page fault
      - Traps – no reexecution needed; e.g. breakpoint
      - Aborts – severe error; process usually terminated (by signal)
    - Programmed exceptions (**software interrupts**)
      - int (system call), int3 (breakpoint)
      - into (overflow), bounds (address check)
