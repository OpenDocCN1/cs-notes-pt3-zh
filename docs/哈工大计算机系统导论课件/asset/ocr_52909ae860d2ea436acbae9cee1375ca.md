# 矩阵乘法总结

```
for (i=0; i<n; i++) {
    for (j=0; j<n; j++) {
        sum = 0.0;
        for (k=0; k<n; k++)
            sum += a[i][k] * b[k][j];
        c[i][j] = sum;
    }
}
```

```
for (k=0; k<n; k++) {
    for (i=0; i<n; i++) {
        r = a[i][k];
        for (j=0; j<n; j++)
            c[i][j] += r * b[k][j];
    }
}
```

```
for (j=0; j<n; j++) {
    for (k=0; k<n; k++) {
        r = b[k][j];
        for (i=0; i<n; i++)
            c[i][j] += a[i][k] * r;
    }
}
```

ijk (& jik):

+   - 2 加载, 0 存储
+   - 不命中率/迭代次数 = 1.25

kij (& ikj):

+   - 2加载, 1存储
+   - 不命中率/迭代次数 = 0.5

jki (& kji):

+   - 2加载, 1存储
+   - 不命中率/迭代次数 = 2.0