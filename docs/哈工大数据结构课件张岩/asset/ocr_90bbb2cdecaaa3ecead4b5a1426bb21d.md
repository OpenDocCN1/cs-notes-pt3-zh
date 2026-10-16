# 4.5 最短路径算法(cont.)

# Floyd算法的实现

```
void Floyd( costtype A[][], costtype C[][], int P[][], int n)
{ for ( i = 0; i < n; i++ )
    for ( j = 0; j < n; j++ ){
        A[i][j] = C[i][j];
        P[i][j] = -1; }
    for ( k = 0; k < n; k++ )
    for ( i = 0; i < n; i++ )
    for ( j = 0; j < n; j++ )
        if ( A[i][k] + A[k][j] < A[i][j] ) {
            A[i][j] = A[i][k] + A[k][j];
            P[i][j] = k;}
}
/* 时间复杂度： O(n³) */
```

Warshall算法

求有向图邻接矩阵C的传递闭包A

A[i][j]=A[i][j]∪(A[i][k]∩A[k][j])；

可以判定有向图任意两点间是否存在有向路。