# NFS Mount Protocol

+   - Following a mount request that conforms to its export list, the server returns a file handle—a key for further accesses
+   - File handle – a file-system identifier, and an inode number to identify the mounted directory within the exported file system
+   - The mount operation changes only the user’s view and does not affect the server side