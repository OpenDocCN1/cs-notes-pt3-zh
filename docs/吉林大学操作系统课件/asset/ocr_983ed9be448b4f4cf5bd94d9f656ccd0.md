# 银行家算法(Cont.)

数据结构：

```
Available: array[1..m]of integer;    //系统可用资源
Claim: array[1..n,1..m]of integer;    //进程最大需求
Allocation: array[1..n,1..m]of integer;    //当前分配
Need: array[1..n,1..m]of integer;    //尚需资源
Request: array[1..n,1..m]of integer;    //当前请求
```

临时变量：

```
Work: array[1..m]of integer;
Finish: array[1..n]of boolean;
```