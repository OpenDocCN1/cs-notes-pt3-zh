再看 n! 的例子。该问题是：当n>0 时，若能计算出 w=(n-1)! 则 r=n!=n*w

```
void fact ( int n , int *r ) {
    int w ;
    if ( n==0 )
        *r = 1 ;
    else {
        fact(n-1,&w);
        *r = n*w
    }
}
```

若把该函数的参数r用函数值表示，就是前边的函数factorial。