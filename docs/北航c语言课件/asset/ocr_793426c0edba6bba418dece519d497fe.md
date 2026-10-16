```
```c
printf(">:%d \n =:%d \n <:%d\n", l, m, n);
if (l>n)    printf("a>b\n");
else if (l<n) printf("a<b\n");
else         printf("a=b\n");
}
```
```

# /* 定义large函数 */

```
```c
int large (int x ,int y)
{
    int flag;
    if (x>y) flag=1;
    else if (x<y) flag=-1;
    else flag = 0;
    return (flag);
}
```
```

| 运行输入： | 运行结果： |
|---|---|
| enter array a:<br>1 3 5 7 9 8 6 4 2 0<br><br>enter array b:<br>5 3 8 9 -1 -3 5 6 0 4 | >: 4<br>=: 1<br><: 5<br>a < b |