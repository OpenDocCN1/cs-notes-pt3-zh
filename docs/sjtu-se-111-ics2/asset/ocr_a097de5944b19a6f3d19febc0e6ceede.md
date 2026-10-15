```
```cpp
for(kk = 0; kk < N; kk+=B)
    for(jj = 0; jj < N; jj+=B)
        for(i = 0; i < N; i++)
            for(k = kk; k < min(kk+B-1,N); k++)
                r = X(i,k);
                for(j = jj; j < min(jj+B-1,N); j++)
                    Z(i,j) += r*Y(k,j);
```
```

![](bbox=[0.239, 0.629, 0.663, 0.855])