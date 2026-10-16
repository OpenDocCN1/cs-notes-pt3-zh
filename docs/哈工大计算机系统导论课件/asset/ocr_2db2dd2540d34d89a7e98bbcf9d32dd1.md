# Switch语句示例

```
long switch_eg(long x, long y, long z)
{
    long w = 1;
    switch(x) {
    ...
    }
    return w;
}
```

| 寄存器 | 用途 |
| --- | --- |
| %rdi | 参数x |
| %rsi | 参数y |
| %rdx | 参数z |
| %rax | 返回值 |

汇编实现：

```
switch_eg:
    movq  %rdx, %rcx
    cmpq  $6, %rdi  # x:6
    ja    .L8
    jmp   *.L4(, %rdi, 8)
```

注意：此处没有w及初始化

属于default的数值范围？