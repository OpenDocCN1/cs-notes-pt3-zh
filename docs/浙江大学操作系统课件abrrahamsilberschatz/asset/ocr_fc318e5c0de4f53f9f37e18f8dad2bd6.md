# # Kernel Synchronization

+   - A request for kernel-mode execution can occur in two ways:
+     - A running program may request an operating system service, either explicitly via a system call, or implicitly, for example, when a page fault occurs.
+     - A device driver may deliver a hardware interrupt that causes the CPU to start executing a kernel-defined handler for that interrupt.
+   - Kernel synchronization requires a framework that will allow the kernel's critical sections to run without interruption by another critical section.