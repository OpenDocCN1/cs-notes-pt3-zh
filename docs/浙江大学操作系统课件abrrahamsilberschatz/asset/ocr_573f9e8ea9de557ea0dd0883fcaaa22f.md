# # Linked Allocation (Cont.)

+   - Simple – need only starting address （简单： 只需要起始地址）
+   - Free-space management system – no waste of space （自由空间管理系统： 没有磁盘空间浪费）
+   - No random access （无法随机存取）
+   - Mapping （映射）

![](bbox=[0.464, 0.446, 0.637, 0.571])

Block to be accessed is the Qth block in the linked chain of blocks representing the file.
Displacement into block = R + 1

File-allocation table (FAT) – disk-space allocation used by MS-DOS and OS/2. （文件分配表： 被MS-DOS和OS/2所采用）