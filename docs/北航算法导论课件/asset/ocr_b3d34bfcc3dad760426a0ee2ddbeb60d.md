# Exercises and problems

# Exercises

分析Fibonacci序列 F(n) = F(n-1) + F(n-2) 如下算法的时间复杂度。

```
f(n)
{
    if(n<=2)
        return 1;
    else
        return f(n-1)+f(n-2);
}
```

```
f1 = 1;
f2 = 1;

for(i=3; i<=n; i++){
    f = f1 + f2;
    f1 = f2;
    f2 = f;
}
```