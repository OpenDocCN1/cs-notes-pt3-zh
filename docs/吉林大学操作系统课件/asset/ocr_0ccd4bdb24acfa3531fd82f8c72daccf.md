# 死锁预防策略

死锁解决方法：同时申请左、右两把叉子（预先分配）。

哲学家状态描述（增加了hunger状态）：

```
State: Array[0..4]Of (thinking,hungry,eating);
```

等待队列设置（每个哲学家一个队列）：

```
Self: Array[0..4]Of semaphore; (initial value is 0);
```