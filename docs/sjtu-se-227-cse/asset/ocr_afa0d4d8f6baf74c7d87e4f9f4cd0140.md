# Address Space Isolation between Threads

+   - Virtual address space
+     - Thread manager is aware of the address space
+     - Switch address space while doing thread switch
+     - ENTER_PROCESSOR_LAYER saves PMAR in the thread_table
+     - EXIT_PROCESSOR_LAYER loads PMAR of the new thread
+   - Sharing thread manager
+     - Map both the instructions and the data of the thread manager into the same set of virtual addresses in every virtual address space