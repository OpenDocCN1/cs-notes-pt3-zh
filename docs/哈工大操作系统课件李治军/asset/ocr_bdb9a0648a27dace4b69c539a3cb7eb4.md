# 进入临界区Peterson算法

+   结合了标记和轮转两种思想

```
flag[0] = true;
turn = 1;
while (flag[1] && turn == 1);
```

临界区

```
flag[0] = false;
```

剩余区

进程P₀

```
flag[1] = true;
turn = 0;
while (flag[0] && turn == 0);
```

临界区

```
flag[1] = false;
```

剩余区

进程P₁

![](bbox=[0.92, 0.71, 0.99, 0.88])