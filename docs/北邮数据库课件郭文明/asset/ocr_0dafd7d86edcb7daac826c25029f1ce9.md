# 4. 2. 1. 1 ORACLE内存结构

+   - SGA组成如下:
+     - 共享池。
+     - 数据库缓冲区高速缓存。
+     - 重做日志缓冲区。

另外oracle9i还有Java pool，8i有Java虚拟机，解释Java；Java pool是利用数据库技术解释Java.

oracle9i的SGA可以通过SGA_MAX_SIZE被动态的设置大小，8i不能动态设置。