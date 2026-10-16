# LoadRunner——测试结果分析

# 磁盘I/O分析方法

+   1. **查看%Disk Time计数器的值。** 该值较大，则可能存在磁盘瓶颈问题。
+   2. **与Processor\Privileged Time合并进行分析。** 若%Disk Time值较大，而Processor\Privileged Time的值适中，则可判断存在磁盘问题。若Processor\Privileged Time较大，持续超过80%，则可能是内存泄漏。
+   3. **根据Disk sec/Transfer进行分析。** 该值超过60ms，则磁盘存在问题。