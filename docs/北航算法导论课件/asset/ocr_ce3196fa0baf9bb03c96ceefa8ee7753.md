# 15.3.1 Optimal substructure : Subtleties

+   - **Independent subproblems in our examples:**
+     - Assembly-line scheduling
+       one optimal subproblem ⇒ automatically independent.
+     - Matrix-chain multiplication
+       two optimal subproblems: $A_i A_{i+1}...A_k$ and $A_{k+1} A_{k+2}...A_j$, independent apparently.
+     - Optimal binary search trees ?

![](bbox=[0.05, 0.68, 0.48, 0.92])

$A_1 A_2 A_3 A_4 A_5 A_6$

((A₁(A₂A₃)) ((A₄A₅)A₆))