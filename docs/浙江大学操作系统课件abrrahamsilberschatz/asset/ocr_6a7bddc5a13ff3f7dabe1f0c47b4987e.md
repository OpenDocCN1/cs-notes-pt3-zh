# # The Linux Proc File System

+   - The proc file system does not store data, rather, its contents are computed on demand according to user file I/O requests.
+   - **proc** must implement a directory structure, and the file contents within; it must then define a unique and persistent inode number for each directory and files it contains.
+     - It uses this inode number to identify just what operation is required when a user tries to read from a particular file inode or perform a lookup in a particular directory inode.
+     - When data is read from one of these files, **proc** collects the appropriate information, formats it into text form and places it into the requesting process’s read buffer.