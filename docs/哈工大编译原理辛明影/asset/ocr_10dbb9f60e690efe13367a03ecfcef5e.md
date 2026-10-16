# 7.10.2 类型转换

x := y + i * j
（x和y的类型是real， i和j的类型是integer）

中间代码

```
t₁ := i int× j
t₂ := inttoreal t₁
t₃ := y real+ t₂
x := t₃
```