# Ext2fs与VFS差别

+   - 存储块管理
+     - FFS采用大块（large block, up to 8K）+碎块（fragment）
+     - Ext2fs 采用统一长度块（1kb,2kb,4kb）
+   - 空闲块管理
+     - Bit map
+     - 使一个文件物理块尽量连续或临近
+     - 预先分配，以确保同一文件所占磁盘块的连续性，未用完磁盘块在文件关闭时释放