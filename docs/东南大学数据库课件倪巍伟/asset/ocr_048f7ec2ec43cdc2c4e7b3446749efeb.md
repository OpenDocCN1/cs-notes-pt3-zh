# 嵌套循环算法

```
/*设R有n个元组，S有m个元组*/
i := 1, j := 1;
while (i ≤ n)
do {
    while (j ≤ m)
    do {
        if R(i)[A] = S(j)[B]
        then 输出<R(i), S(j)>至T;
        j := j + 1
    }
    j := 1, i := i + 1
}
```

![](bbox=[0.732, 0.4, 0.953, 0.596])