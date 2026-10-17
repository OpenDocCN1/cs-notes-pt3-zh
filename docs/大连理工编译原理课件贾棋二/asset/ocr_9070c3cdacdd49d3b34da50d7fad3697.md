# # FIRST集合及FOLLOW集合的计算方法

# ## FOLLOW集合计算方法

+   - 对文法开始符号S,置$于FOLLOW(S)中。

+   - 若有A→αBβ，则将FIRST(β)\{ε} 加入FOLLOW(B)中。（此处α 可以为空）

+   - 若A→α B 或A→α B β,且 β ⇒* ε （即ε 属于FIRST(β)），则将 FOLLOW(A)加入FOLLOW(B)中 （此处α 可以为空）。