# Definability of Minimization

Suppose F computes f(~x,y). Let m be max{n+1, ρ(F)}.

Registers: [...]

Program:

+   I₁ : T(1, m + 1)
+   :
+   Iₙ : T(n, m + n)
+   Iₙ₊₁ : F[m + 1, m + 2, ..., m + n + 1 → 1]
+   Iₙ₊₂ : J(1, m + n + 2, n + 5)
+   Iₙ₊₃ : S(m + n + 1)
+   Iₙ₊₄ : J(1, 1, n + 1)
+   Iₙ₊₅ : T(m + n + 1, 1)