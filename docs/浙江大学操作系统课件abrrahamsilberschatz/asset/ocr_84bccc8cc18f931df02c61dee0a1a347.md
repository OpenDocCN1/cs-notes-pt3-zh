# # 12.2 File System Implementation 文件系统实现

# ## 12.2.1 Overview

+   - The on-disk structures include:
+     - Boot control block
+     - Partition control block(分区控制块): superblock in UFS, Master File Table in NTFS
+     - Directory structure
+     - FCB

+   - In-memory structure include:
+     - In-memory partition table
+     - In-memory directory structure
+     - System-wide open-file table
+     - Per-process open-file table