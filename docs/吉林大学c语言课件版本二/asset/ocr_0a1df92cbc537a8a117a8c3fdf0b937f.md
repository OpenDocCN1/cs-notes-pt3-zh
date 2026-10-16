```
int trans( int e , int f){    /* A[e]~A[f] 翻译成10进制整数 */
    int kk , j ;
    kk=0;
    for ( j=e; j<=f; j++ )
        kk = kk*2 + A[j%nn] ;
    return kk;
}
bool test_b( int kk, int b[], int v){  /* 检验b[0] ~b[v]中有kk */
    int j ;
    for ( j=0; j<v; j++ )
    if ( kk==b[j] )
        return false ;
    return true;
}
```