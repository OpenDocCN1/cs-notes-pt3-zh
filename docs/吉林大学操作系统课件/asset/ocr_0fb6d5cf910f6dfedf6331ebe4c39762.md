# 4.3.3 信号量与PV操作

E.W.Dijkstra, 1965.

# 4.3.3.1 信号量与PV操作的定义

```
Typedef semaphore struct{
    int value;
    PCBpointer queue;
};
semaphore s;
```

Remarks:

+   (1) *semaphore* is pre-defined data type,

+   (2) s can be declared as needed, eg. semaphore s1,s2;