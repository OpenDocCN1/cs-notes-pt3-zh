# WRITE & CLOSE

+   - WRITE is similar to READ
+     - Allocate new block if necessary
+     - Update inode's *size* and *mtime*
+   - CLOSE
+     - Free the entry in the fd_table
+     - Decrease the reference counter in file table
+     - Free the entry in file table if counter is 0
+   - Failures in the middle may cause inconsistency
+     - E.g. a block is allocated from on-disk free list, but no inode records that block yet, then the block is lost