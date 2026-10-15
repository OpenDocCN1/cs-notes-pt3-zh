# Symbolic Link Layer

| Symbolic link |  |  |  |  |
| Absolute path | File name | Inode num | File (inode) | Block num | Disk Block |
| Path name |  |  |  |  |  |

+   - Name files on other disks
+     - Inode is different on other disks
+     - Supports to attach new disks to the name space
+   - Two options
+     - Make inodes unique across all disks ✗
+     - Create synonyms for the files on the other disks
+   - Soft link (symbolic link)
+     - SYMLINK
+     - Add another type of inode
+     - Context: the directory hierarchy