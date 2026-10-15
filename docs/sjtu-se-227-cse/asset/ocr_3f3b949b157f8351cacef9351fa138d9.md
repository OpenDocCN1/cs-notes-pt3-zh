# Microkernel

+   - We would like to keep the kernel small
+   - Reduce the number of bugs
+   - Restrict errors in the module which generates the error
+     - The file manager module error may overwrite kernel data structures unrelated to the file system
+     - Causing unrelated parts of the kernel to fail