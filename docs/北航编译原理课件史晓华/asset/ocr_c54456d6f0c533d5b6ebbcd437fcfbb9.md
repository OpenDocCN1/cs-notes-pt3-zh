# 对于输入表达式 x + y * 3:

```
<expression>
=> <expr>
=> <term><terms>
=> <factor><factors><terms>
=> <variable>ₜₙ@lpₜₙf@phₜⱼ<factors><terms>
=> <variable>ₜₙ@lpₜₙf@phₜⱼ<terms>
=> <variable>ₜₙ@lpₜₙf@phₜⱼ+<term>@add<terms>
=> <variable>ₜₙ@lpₜₙf@phₜⱼ+<factor><factors>@add<terms>
=> <variable>ₜₙ@lpₜₙf@phₜⱼ+<variable>ₜₙ@lpₜₙf@hⱼ*<factors>@add<terms>
=> <variable>ₜₙ@lpₜₙf@phₜⱼ+<variable>ₜₙ@lpₜₙf@hⱼ*<factor>@mul<factors>@add<terms>
=> <variable>ₜₙ@lpₜₙf@phₜⱼ+<variable>ₜₙ@lpₜₙf@hⱼ*<integer>ₜᵢ@phiⱼ@mul<factors>@add<terms>
=> <variable>ₜₙ@lpₜₙf@phₜⱼ+<variable>ₜₙ@lpₜₙf@hⱼ*<integer>ₜᵢ@phiⱼ@mul@add<terms>
=> <variable>ₜₙ@lpₜₙf@phₜⱼ+<variable>ₜₙ@lpₜₙf@phₜⱼ*<integer>ₜᵢ@phiⱼ@mul@add
```

+   1. <expression> → <expr>
+   2. <expr> → <term><terms>
+   3. <terms> → ε
+   4.      | +<term>@add<terms>
+   5.      | -<term>@sub<terms>
+   6. <term> → <factors><factors>
+   7. <factors> → ε
+   8.      | *<factor>@mul<factors>
+   9.      | /<factor>@div<factors>
+   10. <factor> → <variable>ₜₙ@lookupₜₙⱼ @pushᵢⱼ
+   11.      | <integer>ₜᵢ@pushᵢⱼ
+   12.      | (<expr>)

+   LOD, < ll, on> x
+   LOD, < ll, on> y
+   LDC, 3
+   MUL
+   ADD