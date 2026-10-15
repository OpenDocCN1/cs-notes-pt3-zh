# File Meta-data

+   - Owner ID
+     - User ID and group ID that own this inode
+   - Types of permission
+     - Owner, group, other
+     - Read, write, execute
+   - Time stamps
+     - Last access (by OPEN)
+     - Last modification (by WRITE)
+     - Last change of inode (by LINK)

```
structure inode
  integer block_numbers[N]
  integer size
  integer type
  integer refcnt
  integer userid
  integer groupid
  integer mode
  integer atime
  integer mtime
  integer ctime
```