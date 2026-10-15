# Matrix multiplication (kji)

```
```c
/* kji */
for (k=0; k<n; k++) {
  for (j=0; j<n; j++) {
    r = b[k][j];
    for (i=0; i<n; i++)
      c[i][j] += a[i][k] * r;
  }
}
```
```

![](bbox=[0.56, 0.29, 0.92, 0.74])

# Misses per Inner Loop Iteration:

| A | B | C | Summary |
|---:|---:|---:|---|
| 1.0 | 0.0 | 1.0 | 2 loads, 1 store; misses/iter = 2.0 |