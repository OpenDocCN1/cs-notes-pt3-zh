# Virtual Memory (Cont.)

+   - On executing a new program, the process is given a new, completely empty virtual-address space; the program-loading routines populate the address space with virtual-memory regions.
+   - Creating a new process with **fork** involves creating a complete copy of the existing process’s virtual address space.
+     - The kernel copies the parent process’s VMA descriptors, then creates a new set of page tables for the child.
+     - The parent’s page tables are copied directly into the child’s, with the reference count of each page covered being incremented.
+     - After the fork, the parent and child share the same physical pages of memory in their address spaces.