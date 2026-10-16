# SMP上的线程调度

+   - 线程与CPU的亲合关系
+     - 每个进程有一个处理器亲合掩码，缺省为所有处理器的集合
+     - 线程继承其进程的亲合掩码
+     - 亲合掩码可以修改
+       - SetProcessAffinityMask,
+       - SetThreadAffinityMask;