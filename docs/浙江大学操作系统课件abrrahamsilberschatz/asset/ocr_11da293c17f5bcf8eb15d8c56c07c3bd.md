# # 8.4 Deadlock Prevention

# # 死锁的预防

Restrain the ways request can be made.
抑制死锁发生的必要条件

+   8.4.1 Mutual Exclusion – not required for sharable resources; must hold for nonsharable resources.
+   互斥：共享资源不是必须的，必须保持非共享资源

+   8.4.2 Hold and Wait – must guarantee that whenever a process requests a resource, it does not hold any other resources.占有并等待： 必须保证进程申请资源的时候没有占有其他资源

+   Require process to request and be allocated all its resources before it begins execution, or allow process to request resources only when the process has none.要求进程在执行前一次申请全部的资源，只有没有占有资源时才可以分配资源