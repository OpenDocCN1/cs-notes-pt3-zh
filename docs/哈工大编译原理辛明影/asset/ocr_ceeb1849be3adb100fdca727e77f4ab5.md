# 图5-26 表达式9-5+2的计算

```
E→T {R·i:=T·val}
R{E·val:=R·s}
R→+T{R₁·i:=R·i+T.val}
R₁{R·s:=R₁·s}
R→-T{R₁·i:=R·i-T.val}
R₁{R·s:=R₁·s}
R→ε {R·s:=R·i}
T→(E){T·val:=E.val}
T→num {T·val:=num.val}
```

![](bbox=[0.02, 0.15, 0.62, 0.98])