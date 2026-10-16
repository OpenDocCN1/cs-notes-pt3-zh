# Useful Big-O Estimates Involving Logarithms, Powers, and Exponents

+   - If $d > c > 1$, then
+     $n^c$ is $O(n^d)$, but $n^d$ is not $O(n^c)$.
+   - If $b > 1$ and $c$ and $d$ are positive, then
+     $(\log_b n)^c$ is $O(n^d)$, but $n^d$ is not $O((\log_b n)^c)$.
+   - If $b > 1$ and $d$ is positive, then
+     $n^d$ is $O(b^n)$, but $b^n$ is not $O(n^d)$.
+   - If $c > b > 1$, then
+     $b^n$ is $O(c^n)$, but $c^n$ is not $O(b^n)$.