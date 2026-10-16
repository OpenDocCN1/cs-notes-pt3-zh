# 函数 sort 如下：

```
void sort ( int n, int a[] ) {
    int i, j, k, r ;
    for ( i=0 ; i<n-1 ; i++ ) {
        j=i ;
        for ( k=i+1 ; k<n ; k++ )
            if ( a[k] < a[j] )
                j=k ;
        r = a[i] ;
        a[i] = a[j] ;
        a[j] = r ;
    }
}
```