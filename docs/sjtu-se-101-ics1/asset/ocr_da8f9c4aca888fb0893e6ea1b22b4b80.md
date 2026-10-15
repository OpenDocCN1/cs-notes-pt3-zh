# Matrix multiplication (ikj)

```
/* ikj */
for (i=0; i<n; i++) {
    for (k=0; k<n; k++) {
        r = a[i][k];
        for (j=0; j<n; j++)
            c[i][j] += r * b[k][j];
    }
}
```

![](bbox=[0.58, 0.25, 0.95, 0.62])

+   - Misses per Inner Loop Iteration:

A   B   C   2 loads, 1 store
0.0 0.25 0.25 misses/iter = 2.0