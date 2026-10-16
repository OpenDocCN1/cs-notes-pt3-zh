# 分块矩阵乘法

```
c = (double *) calloc(sizeof(double), n*n);

/* Multiply n x n matrices a and b */
void mmm(double *a, double *b, double *c, int n)
{ int i, j, k;
for (i = 0; i < n; i+=B) for
(j = 0; j < n; j+=B)
for (k = 0; k < n; k+=B)
/* B x B mini matrix multiplications */
*/ for (i1 = i; i1 < i+B; i++)
for (j1 = j; j1 < j+B; j++) for
(k1 = k; k1 < k+B; k++)
c[i1*n+j1] += a[i1*n + k1]*b[k1*n + j1];
}
```

![](bbox=[0.05, 0.72, 0.85, 0.96])