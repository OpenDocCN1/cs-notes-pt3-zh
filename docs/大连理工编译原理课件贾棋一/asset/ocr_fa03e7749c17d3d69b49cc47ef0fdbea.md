# # 3.5 LR分析器

![](bbox=[0.047, 0.094, 0.312, 0.977])

I₄:
F→(·E)
E→·E+T
E→·T
T→·T*F
T→·F
F→·(E)
F→·id

I₈:
F→(E·)
E→E·+T

I₂:
E→T·
T→T·*F

I₃:
T→F·

I₄:
F→(·E)
...

| 产生式 |
|--------|
| E' → E |
| E → E + T | T |
| T → T * F | F |
| F → ( E ) | id |