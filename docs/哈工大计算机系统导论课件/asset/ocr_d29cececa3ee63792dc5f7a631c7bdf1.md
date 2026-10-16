# 内存相关妨碍优化

```
/* Sum rows is of n X n matrix a
and store in vector b */
void sum_rows1(double *a, double *b, long n) {
    long i, j;
    for (i = 0; i < n; i++) {
        b[i] = 0;
        for (j = 0; j < n; j++)
            b[i] += a[i*n + j];
    }
}
```

```
# sum_rows1 inner loop
.L4:
    movsd  (%rsi,%rax,8), %xmm0   # FP load
    addsd  (%rdi), %xmm0          # FP add
    movsd  %xmm0, (%rsi,%rax,8)   # FP store
    addq   $8, %rdi
    cmpq   %rcx, %rdi
    jne    .L4
```

+   - 代码每次循环都更新 b[i]
+   - 为什么编译器不能优化这个？