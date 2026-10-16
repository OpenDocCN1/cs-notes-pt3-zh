# 7.11 文件系统的效率



write is postponed until absolutely necessary

+   - no free buffer
+   - upon file close (all user close, i_count=0)
+   - system flush



allocating contiguous disk blocks to a file

+   - request to access disk are served in scan order