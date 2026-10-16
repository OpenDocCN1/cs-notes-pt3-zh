# 实例: incr

```
long incr(long *p, long val) {
    long x = *p;
    long y = x + val;
    *p = y;
    return x;
}
```

```
incr:
    movq    (%rdi), %rax
    addq    %rax, %rsi
    movq    %rsi, (%rdi)
    ret
```

| 寄存器 | 用途 |
| --- | --- |
| %rdi | 参数 p |
| %rsi | 参数 val, y |
| %rax | x, 返回值 |