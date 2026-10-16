# 算符优先关系矩阵的构造

+   - A→...ab...；A→...aBb..., 则 a ≡ b
+   - A→...aB...,则对∀b ∈ FIRSTOP(B), a < b
+   - A→...Bb...,则对∀a ∈ LASTOP(B), a > b
+   - 求FIRSTOP的算法
+   - 1.若有产生式，A→a... 或 A→Ba..., 则
+     a∈FIRSTOP(A)
+   - 2.if A→B... ∈ P, then FIRSTOP(B) ⊆ FIRSTOP(A)
+   - 同理，可构造LASTOP的算法