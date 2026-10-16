# 【Example】 Matrix addition

```
void add( int a[][ MAX_SIZE ],
    int b[][ MAX_SIZE ],
    int c[][ MAX_SIZE ],
    int rows, int cols )
{
    int i, j;
    for( i = 0; i < rows; i++ )  /* Θ (rows) */
        for( j = 0; j < cols; j++ )  /* Θ (rows * cols) */
            c[i][j] = a[i][j] + b[i][j];  /* Θ (rows * cols) */
}
```

T(rows, cols) = Θ (rows * cols)