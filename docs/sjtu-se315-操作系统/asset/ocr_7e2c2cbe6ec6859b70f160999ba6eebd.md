# Xv6's simple logging

FS has a log on disk syscall:

+   - begin_trans()
+   - bp = bread()
+   - bp->data[] = ...
+   - log_write(bp)
+   - more writes ...
+   - commit_trans()

![](bbox=[0.12, 0.56, 0.92, 0.75])