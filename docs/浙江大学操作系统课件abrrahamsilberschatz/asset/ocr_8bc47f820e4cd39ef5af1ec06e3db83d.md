# Disk Scheduling (Cont.)

+   - Minimize seek time　最小寻道时间
+   - Seek time ≈ seek distance　寻道时间 ≈ 寻道距离

Disk bandwidth is the total number of bytes transferred, divided by the total time between the first request for service and the completion of the last transfer.

磁盘带宽，是用传输的总位数，除以第一个服务请求与最后传输完成之间的总时间。

+   - Several algorithms exist to schedule the servicing of disk I/O requests.
+   
+     有几种磁盘I/O请求的服务调度算法

+   - We illustrate them with a request queue (0–199).
+   
+     98, 183, 37, 122, 14, 124, 65, 67
+   
+     Head pointer 53