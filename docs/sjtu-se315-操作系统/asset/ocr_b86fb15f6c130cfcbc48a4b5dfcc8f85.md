# Using a File as Shared Memory

+   - mmap system call can be used to map a file to a process's virtual memory address space.
+   - In many ways mmap is more flexible than its shared memory system call counterpart.
+   - Once a mapping has been established, standard system calls rather than specialized system calls can be used to manipulate the shared memory object.
+   - Unlike memory, the contents of a file are nonvolatile and will remain available even after a system has been shut down (and rebooted).