# Definability of Recursion

Let F compute f and G compute g. Let m be max{n, ρ(F), ρ(G)}.

Registers: [...]

Program:

+   I₁ : T(1, m + 1)
+   :
+   Iₙ₊₁ : T(n + 1, m + n + 1)
+   Iₙ₊₂ : F[1, 2, ..., n → m + n + 3]
+   Iₙ₊₃ : J(m + n + 2, m + n + 1, n + 7)
+   Iₙ₊₄ : G[m + 1, ..., m + n, m + n + 2, m + n + 3 → m + n + 3]
+   Iₙ₊₅ : S(m + n + 2)
+   Iₙ₊₆ : J(1, 1, n + 3)
+   Iₙ₊₇ : T(m + n + 3, 1)