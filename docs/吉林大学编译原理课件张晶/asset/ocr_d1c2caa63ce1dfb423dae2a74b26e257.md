# 静态存储分配实例

```
int sum = 0;
int square(int i)
{
    int j;
    j = i * i;
    return j;
}
void main()
{
    int j;
    j = square(n);
    sum = sum + j;
}
```

```
(ENTRY, L_sqr, 3+off, 1)
(*, i, i, t₁)
(assig, t₁, _, j)
(RETURN, _, _, j)
(ENDFUN, _, _, _)
(ENTRY, L_main, 3+off, 1)
(VALACT, n, off_i, 1)
(call, square, true, t₂)
(assig, t₂, 1, j)
(+, sum, j, t₃)
(assig, t₃, 1, sum)
(ENDFUNC, _, _, _)
```

| 目标代码 |
| sum |
| 常量信息表等... |
| square的控制信息 ... |
| i |
| j |
| t₁ |
| main的控制信息 ...... |
| j |
| t₂ |
| t₃ |