```
int nn;                         // 记录环的长度
int A[ 256 ];                   /* 保存环,限制输入 n 最大为 8 */
bool check( int u );            /* 检查A[0]~A[u]的个n位整数是否不同，略 */
void  out();                    /* 输出A数组，略 */
int power(int w );              /* 求 nn，略 */
void  next( int m ){            /* 枚举 */
    int i;
    if( m < nn )
        for( i=0; i<=1; i++ ){
            A[m] = i;
            next( m+1 );
        }
    else if( check(nn-1) )      // 检验合格
        out();
}
int main(void){                 /* 主程序 */
    int n ;
    printf("\n pleace input n="); scanf( "%d", &n );  /* 输入n<=8 */
    nn=power(n);                /* 求nn */
    next(0);
}
```