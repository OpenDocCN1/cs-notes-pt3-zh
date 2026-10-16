我们设想，若有一个函数

combination ( s , j )

能够完成从自然数序列中，取 j 个数作组合

s , s+1 , s+2 , ... , n

则我们的原始问题可以写成函数调用：

combination ( 1 , r )

而我们的分析算法则可以写成：

```
for i = 1 TO n-r+1 DO
```

```
combination ( i+1 , r-1 )
```