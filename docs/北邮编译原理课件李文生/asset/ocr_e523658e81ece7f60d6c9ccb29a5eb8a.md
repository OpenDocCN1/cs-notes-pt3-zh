# 布尔表达式的代码结构

E→ E₁ or E₂

E→ not E₁

E→ E₁ and E₂

E→ id₁ relop id₂

![](bbox=[0.06, 0.26, 0.38, 0.57])

![](bbox=[0.47, 0.26, 0.84, 0.42])

![](bbox=[0.06, 0.62, 0.38, 0.93])

```
'if' id₁.place relop.op id₂.place 'goto' E.true
'goto' E.false
```