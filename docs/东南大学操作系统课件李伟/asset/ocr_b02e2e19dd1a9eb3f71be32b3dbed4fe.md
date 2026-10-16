# # Fragmentation(碎片)

+   - Processes are loaded and removed from memory, eventually the memory will be cut into small holes that are not large enough to run any incoming process.
+   - Free memory holes between allocated ones are called **_external fragmentation_**.
+   - It is unwise to allocate exactly the requested amount of memory to a process, **because of the minimum requirement for memory management**.
+   - Thus, memory that is allocated to a partition, but is not used, are called **_internal fragmentation_**.