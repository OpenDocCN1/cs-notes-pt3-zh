# 14.2.6 Selecting a Disk-Scheduling Algorithm
选择一种磁盘调度算法

+   - SSTF is common and has a natural appeal
+     SSTF比较通用，性能一般。
+   - SCAN and C-SCAN perform better for systems that place a heavy load on the disk.
+     SCAN和C-SCAN在重磁盘负载的系统中性能较好。
+   - Performance depends on the number and types of requests.
+     性能依赖于请求的数量和类型。
+   - Requests for disk service can be influenced by the file-allocation method.
+     磁盘服务请求受到文件定位方式的影响。