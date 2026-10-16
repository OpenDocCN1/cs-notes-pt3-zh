# 3.2 消除直接左递归

+   ◆ 例子
+   E → E+T | T
+   T → T * F | F
+   F → ( E ) | i

```
A→Aα|β
E→E+T | T
α=+T  β=T
E→TE'
E'→+TE'|ε
```

```
E→TE'
E'→+TE'|ε
T→FT'
T'→*FT'|ε
F→(E)|i
```