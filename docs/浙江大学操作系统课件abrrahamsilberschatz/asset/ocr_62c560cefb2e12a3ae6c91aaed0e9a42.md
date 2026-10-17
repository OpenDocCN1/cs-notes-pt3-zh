# # 8.5 Deadlock Avoidance 死锁避免

Requires that the system has some additional
a priori information available.需要系统有一些额外的信息

+   Simplest and most useful model requires that each process declare the *maximum number* of resources of each type that it may need.
+   一个简单而有效的模型要求每一个进程声明它所需要的资源的最大数

+   The deadlock-avoidance algorithm dynamically examines the resource-allocation state to ensure that there can never be a circular-wait condition.
+   死锁避免算法动态检查资源分配状态以确保不会出现循环等待的情况