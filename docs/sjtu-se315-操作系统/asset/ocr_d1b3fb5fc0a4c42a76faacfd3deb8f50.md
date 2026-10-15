# What Does fsck do?

+   - 1. Check superblock
+     - E.g., making sure the file system size is greater than the number of blocks allocated
+     - If error, use an alternate copy of the superblock
+   - 2. Check free blocks
+     - Scans the inodes, indirect blocks, double indirect blocks, etc.
+     - Uses this knowledge to produce a correct version of the allocation bitmaps
+     - Same for the inode bitmap