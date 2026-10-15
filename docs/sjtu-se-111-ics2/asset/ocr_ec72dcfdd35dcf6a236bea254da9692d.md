# Context switching

+   - The kernel maintains a context for each process
+   - The context is the state that the kernel needs to restart a preempted process
+   - Context contains
+     - Value of PC, register file, status registers, user's stack, kernel's stack
+     - Kernel data structures
+       - Process table, page table, file table