# # 14.1 Disk Structure磁盘结构

+   Disk drives are addressed as large 1-dimensional arrays of _logical blocks_, where the logical block is the smallest unit of transfer.
+   磁盘设备是以一种逻辑块的一维大数组的形式编址的，这里的逻辑块是传输的最小单位。

+   The 1-dimensional array of logical blocks is mapped into the sectors of the disk sequentially.
+   逻辑块的一维数组映射到磁盘上一些相连的扇区。

+   Sector 0 is the first sector of the first track on the outermost cylinder.
+   0扇区是最外边柱面的第一个磁道的第一个扇区。

+   Mapping proceeds in order through that track, then the rest of the tracks in that cylinder, and then through the rest of the cylinders from outermost to innermost. 数据首先都映射到一个磁道，其余的数据映射到同一柱面的其他磁道，然后按照从外向里的顺序映射到其余的柱面。