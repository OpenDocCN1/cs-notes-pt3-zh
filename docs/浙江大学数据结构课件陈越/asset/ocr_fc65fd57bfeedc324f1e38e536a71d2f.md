# 例3：写程序计算给定多项式 \( f(x) = \sum_{i=0}^{9} i \cdot x^i \) 在给定点 \( x = 1.1 \) 处的值 \( f(1.1) \)

```
double f1( int n, double a[], double x )
{
    int i;
    double p = a[0];
    for ( i=1; i<=n; i++ )
        p += (a[i] * pow(x, i));
    return p;
}
```

```
double f2( int n, double a[], double x )
{
    int i;
    double p = a[n];
    for ( i=n; i>0; i-- )
        p = a[i-1] + x*p;
    return p;
}
```