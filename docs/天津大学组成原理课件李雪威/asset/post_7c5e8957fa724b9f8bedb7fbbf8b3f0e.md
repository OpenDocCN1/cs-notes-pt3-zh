

## Matrix Multiplication (kji)

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

Inner loop:
- A: Column-wise
- B: Fixed
- C: Column-wise

Misses per inner loop iteration:

|   | A   | B   | C   |
|---|-----|-----|-----|
|   | 1.0 | 0.0 | 1.0 |

Block size = 32B (four doubles)

## Summary of Matrix Multiplication

```cpp
for (i=0; i<n; i++) {
    for (j=0; j<n; j++) {
        sum = 0.0;
        for (k=0; k<n; k++)
            sum += a[i][k] * b[k][j];
        c[i][j] = sum;
    }
}
```

```cpp
for (k=0; k<n; k++) {
    for (i=0; i<n; i++) {
        r = a[i][k];
        for (j=0; j<n; j++)
            c[i][j] += r * b[k][j];
    }
}
```

```cpp
for (j=0; j<n; j++) {
    for (k=0; k<n; k++) {
        r = b[k][j];
        for (i=0; i<n; i++)
            c[i][j] += a[i][k] * r;
    }
}
```

### ijk (& jik):
- 2 loads, 0 stores
- misses/iter = 1.25

### kij (& ikj):
- 2 loads, 1 store
- misses/iter = 0.5

### jki (& kji):
- 2 loads, 1 store
- misses/iter = 2.0

## Core i7 Matrix Multiply Performance

Cycles per inner loop iteration

![](img/be2cf0737cec89669e7b18813ea2d3b7_605_0.png)

Array size (n)

## Today

- Cache organization and operation
- Performance impact of caches
  - The memory mountain
  - Rearranging loops to improve spatial locality
  - Using blocking to improve temporal locality

## Example: Matrix Multiplication

```c
c = (double *) calloc(sizeof(double), n*n);
/* Multiply n x n matrices a and b */
void mmm(double *a, double *b, double *c, int n) {
    int i, j, k;
    for (i = 0; i < n; i++)
        for (j = 0; j < n; j++)
            for (k = 0; k < n; k++)
                c[i*n + j] += a[i*n + k] * b[k*n + j];
}
```

![](img/be2cf0737cec89669e7b18813ea2d3b7_607_0.png)

## Cache Miss Analysis

### Assume:
- Matrix elements are doubles
- Cache block = 8 doubles
- Cache size C << n (much smaller than n)

### First iteration:
- n/8 + n = 9n/8 misses
- Afterwards in cache: (schematic)

![](img/be2cf0737cec89669e7b18813ea2d3b7_608_0.png)

## Blocked Matrix Multiplication

```c
c = (double *) calloc(sizeof(double), n*n);

/* Multiply n x n matrices a and b */
void mmm(double *a, double *b, double *c, int n) {
    int i, j, k;
    for (i = 0; i < n; i+=B)
        for (j = 0; j < n; j+=B)
            for (k = 0; k < n; k+=B)
                /* B x B mini matrix multiplications */
                for (il = i; il < i+B; i++)
                    for (jl = j; jl < j+B; j++)
                        for (kl = k; kl < k+B; k++)
                            c[il*n+jl] += a[il*n + kl]*b[kl*n + jl];
}
```

![](img/be2cf0737cec89669e7b18813ea2d3b7_610_0.png)

## Cache Miss Analysis

### Assume:
- Cache block = 8 doubles
- Cache size C << n (much smaller than n)
- Three blocks fit into cache: 3B² < C

### First (block) iteration:
- B²/8 misses for each block
- 2n/B x B²/8 = nB/4 (omitting matrix c)
- Afterwards in cache (schematic)

![](img/be2cf0737cec89669e7b18813ea2d3b7_611_0.png)
![](img/be2cf0737cec89669e7b18813ea2d3b7_611_1.png)
![](img/be2cf0737cec89669e7b18813ea2d3b7_611_2.png)
![](img/be2cf0737cec89669e7b18813ea2d3b7_611_3.png)
![](img/be2cf0737cec89669e7b18813ea2d3b7_611_4.png)
![](img/be2cf0737cec89669e7b18813ea2d3b7_611_5.png)

n/B blocks

Block size B x B

Bryant and O'Hallaron, Computer Systems: A Programmer's Perspective, Third Edition

51

## Cache Miss Analysis

### Assume:
- Cache block = 8 doubles
- Cache size C << n (much smaller than n)
- Three blocks fit into cache: 3B² < C

### Second (block) iteration:
- Same as first iteration
- 2n/B x B²/8 = nB/4

### Total misses:
- nB/4 * (n/B)² = n³/(4B)

![](img/be2cf0737cec89669e7b18813ea2d3b7_612_0.png)

