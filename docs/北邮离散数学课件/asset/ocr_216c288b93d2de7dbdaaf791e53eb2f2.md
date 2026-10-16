# Second Principle of Induction

A.k.a. “Strong Induction”

+   - Characterized by another inference rule:
+     $P(0)$
+     $P$ is true in *all* previous cases
+     $\forall n\ge0: (\forall 0\le k\le n\ P(k)) \rightarrow P(n+1)$
+     $\therefore \forall n\ge0: P(n)$

+   - The only difference between this and the 1st principle is that:
+     - the inductive step here makes use of the stronger hypothesis that $P(k)$ is true for *all* smaller numbers $k<n+1$, not just for $k=n$.