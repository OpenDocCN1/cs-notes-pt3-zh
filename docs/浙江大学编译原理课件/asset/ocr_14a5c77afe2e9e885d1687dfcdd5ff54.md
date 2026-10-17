# 4.2.3 left Recursion Removal and Left Factoring

2、 Left factoring:

Left factoring is required when two or more grammar rule choices share a common prefix string,

A→ α β  |  α γ

![](bbox=[0.399, 0.365, 0.476, 0.416])

```
A→αA′
A′→ β | γ
```

Example:

```
Stmt-sequence→stmt; stmt-sequence | stmt
Stmt→s
```

![](bbox=[0.781, 0.668, 0.999, 0.999])

![](bbox=[0.004, 0.909, 0.095, 0.993])