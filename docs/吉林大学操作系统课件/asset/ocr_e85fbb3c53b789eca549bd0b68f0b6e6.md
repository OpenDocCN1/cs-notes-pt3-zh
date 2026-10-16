# SMP上的线程调度

+   - 线程的理想处理器（Ideal processor）
+     - 首选处理器：
+     - 第二处理器：（在内核线程控制块中）
+   - 理想处理器确定
+     - 线程创建时随机确定，
+     - 分散各个线程与处理机对应关系。
+     - 线程可修改SetThreadIdealProcessor