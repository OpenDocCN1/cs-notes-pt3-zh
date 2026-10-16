# 例8-16 n 次勒让德多项式

pₙ(x) = { 1 当 n = 0
x 当 n = 1
((2n-1)x pₙ₋₁(x) - (n-1) pₙ₋₂(x)) / n 当 n > 1 }

计算它的递归函数是：

```
float p ( int n , float x ) {
    if ( n==0 )
        return 1 ;
    else
        if (n==1)
            return x ;
        else
            return ( (2*n-1)*x*p(n-1,x) - (n-1)*p(n-2,x) )/n ;
}
```