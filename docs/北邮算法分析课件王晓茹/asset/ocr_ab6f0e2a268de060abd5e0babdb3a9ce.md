# 【Example】 Matrix addition

```
void add( int a[][ MAX_SIZE ],
            int b[][ MAX_SIZE ],
            int c[][ MAX_SIZE ],
            int rows, int cols )
{
    int i, j;
    for( i = 0; i < rows; i++ )  /* rows + 1 */
        for( j = 0; j < cols; j++ )  /* rows(cols+1) */
            c[i][j] = a[i][j] + b[i][j];  /* rows · cols */
}
```

A: Exchange rows and cols.

T(rows, cols) = 2 rows · cols + 2rows + 1