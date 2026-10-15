# Review: File Cursor Sharing

![](bbox=[0.11, 0.26, 0.94, 0.68])

+   - Process A, B and C all open just one file with inode number 23
+   - Process A and B open the same file, not share file cursor
+   - Process B and C share the file cursor