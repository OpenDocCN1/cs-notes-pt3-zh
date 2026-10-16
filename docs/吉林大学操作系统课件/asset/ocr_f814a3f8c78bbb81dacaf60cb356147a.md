# Solution1: 不考虑R-R不互斥

```
Var r_w_w:semaphore; (init value: 1)
```

Reader:

```
P(r_w_w);
{读操作}
V(r_w_w);
```

Writer:

```
P(r_w_w)
{写操作}
V(r_w_w)
```

分析：（1）写者活动正确；（2）R-R不能同时。

改进：最先进入的R执行P；最后离开的R执行V；