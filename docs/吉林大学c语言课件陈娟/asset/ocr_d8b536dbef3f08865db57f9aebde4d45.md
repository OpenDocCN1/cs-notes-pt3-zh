# 例8-16 n 次勒让德多项式

```
p_n(x) = \begin{cases} 1 & \text{当 n=0} \\ x & \text{当 n=1} \\ \frac{((2n-1)x p_{n-1}(x) - (n-1)p_{n-2}(x))}{n} & \text{当 n>1} \end{cases}
```

计算它的递归函数是：

```
float p (int n, float x) {
 if ( n==0 )
 return 1 ;
 else
 if (n==1)
 return x ;
 else
 return ( (2*n-1)*x*p(n-1,x) - (n-1)*p(n-2,x) )/n ;
}
```