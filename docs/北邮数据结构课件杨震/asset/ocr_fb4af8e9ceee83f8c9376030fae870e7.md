# 顺序搜索（Sequential Search）

```
int seqsearch ( int a[], const int n,
                 const int x )    //a[0],...,a[n-1]
{
    int i = 0;
    while ( i < n && a[i] != x )
        i++;
    if ( i == n ) return -1;
    return i;
}
```