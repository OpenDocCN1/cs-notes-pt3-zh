# 间接引用坏指针

+   经典的scanf错误

```
int val;
...
scanf("%d", val);//应当&val
```

从stdin读一个整数到一个变量val
正确方法：传递变量的地址给scanf