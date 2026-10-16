# Savitch’s Theorem

+   CANYIELD = “On input $c_1$, $c_2$ and $t$:
+   1. If $t = 1$, then test directly whether $c_1 = c_2$ or whether $c_1$ yields $c_2$ in one step by $N$. Accept if either one test succeeds; reject otherwise.
+   2. If $t > 1$, then for each configuration $c_m$ of $N$ on $w$ using space $f(n)$:
+      3. Run CANYIELD($c_1$, $c_m$, $t/2$)
+      4. Run CANYIELD($c_m$, $c_2$, $t/2$)
+      5. If steps 3 and 4 both accept, then accept
+   6. If have not yet accepted, reject”