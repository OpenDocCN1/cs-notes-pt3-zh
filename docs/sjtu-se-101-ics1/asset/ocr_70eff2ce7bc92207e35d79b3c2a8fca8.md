# Stride-1 reference pattern

```
int sumarrayrows(int a[M][N])
{
    int i, j, sum = 0 ;

    for (i = 0 ; i < M ; i++)
        for ( j = 0 ; j < N ; j++ )
            sum += a[i][j] ;
    return sum ;
}
```

| Address | 0 | 4 | 8 | 12 | 16 | 20 |
|---|---|---|---|---|---|---|
| Contents | a₀₀ | a₀₁ | a₀₂ | a₁₀ | a₁₁ | a₁₂ |
| Access order | 1 | 2 | 3 | 4 | 5 | 6 |