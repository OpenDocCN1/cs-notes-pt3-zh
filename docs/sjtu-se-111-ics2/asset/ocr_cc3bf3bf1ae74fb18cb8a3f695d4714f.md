# Open Files

+   - An application announces its intention to access an I/O device
+     - The kernel opens the corresponding file
+     - The kernel returns a small non-negative integer, descriptor
+       - Identifies the file in all subsequent operations on the file
+     - The kernel keeps track of all information about the open file
+       - Maintains a file position k, initially 0, for each open file