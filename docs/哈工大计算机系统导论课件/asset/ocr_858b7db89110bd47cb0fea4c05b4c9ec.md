# 结构体成员地址的生成

```
struct rec {
    int a[4];
    size_t i;
    struct rec *next;
};
```

![](bbox=[0.48, 0.2, 0.88, 0.38])

# 数组元素的地址

+   - 每个结构体成员的偏移量(Offset)是在编译阶段确定的
+   - 地址计算形式:
+     r + 4*idx

```
int *get_ap
(struct rec *r, size_t idx)
{
    return &r->a[idx];
}
取a[idx]的地址
```

```
# r in %rdi, idx in %rsi
leaq (%rdi,%rsi,4), %rax
ret
```