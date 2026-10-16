# 5.2 数组的顺序存储结构

一维数组

```
elemtype a[1,..,n]
```

b → 基地地址
 a[1]
 a[2]
 a[i]
 } c个单元

loc(a[i])=b+(i-1)c
 =b-c+i*c
 =C₀+C₁*i

C₁=c
 C₀=b- C₁