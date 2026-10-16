# 递归举例

例2 Fibonacci数列

无穷数列1, 1, 2, 3, 5, 8, 13, 21, 34, 55, …, 被称为Fibonacci数列。它可以递归地定义为：

F(n) = { 1    n = 0
          1    n = 1
          F(n-1) + F(n-2)    n > 1 }

边界条件

递归方程

第n个Fibonacci数可递归地计算如下：

```
public static int fibonacci(int n)
{
    if (n <= 1) return 1;
    return fibonacci(n-1)+fibonacci(n-2);
}
```