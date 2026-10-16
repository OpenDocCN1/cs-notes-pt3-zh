# 访问数组元素

+   - 计算数组元素的offset: 12*idx
+     - sizeof(S3)，包括对齐引入的空白
+   - 字段j在结构体内的offset: 8
+   - 汇编器给出的offset: a+8
+     - a:链接时确定

```
struct S3 {
    short i;
    float v;
    short j;
} a[10];
```

![](bbox=[0.05, 0.55, 0.9, 0.85])

```
short get_j(int idx)
{
    return a[idx].j;
}
```

```
# %rdi = idx
leaq (%rdi,%rdi,2),%rax # 3*idx
movzwl a+8,(%rax,4),%eax
```