# 下面的优化合理吗？

```
int foo(int a)
{
    int count = 0 ;
    for(int i = 1 ; i<=100 ; i++){
        count += i ;
    }
    return a + count ;
}
```

```
int foo(int a)
{
    return a + 5050 ;
}
```

![](bbox=[0.52, 0.38, 0.62, 0.5])