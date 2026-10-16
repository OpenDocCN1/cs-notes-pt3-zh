# Lamé Proof, continued

+   - Since $r_0 \ge r_1 > r_2 > \dots > r_n$, each quotient $q_i \equiv \lfloor r_{i-1}/r_i \rfloor \ge 1$.
+   - Since $r_{n-1} = r_n q_n$ and $r_{n-1} > r_n$, $q_n \ge 2$.
+   - So we have the following relations between $r$ and $f$:
+     $r_n \ge 1 = f_2$
+     $r_{n-1} \ge 2r_n \ge 2f_2 = f_3$
+     $r_{n-2} \ge r_{n-1} + r_n \ge f_2 + f_3 = f_4$
+     ...
+     $r_2 \ge r_3 + r_4 \ge f_{n-1} + f_{n-2} = f_n$
+     $b = r_1 \ge r_2 + r_3 \ge f_n + f_{n-1} = f_{n+1}$.
+   - Thus, if $n>2$ divisions are used, then $b \ge f_{n+1} > \alpha^{n-1}$.
+     - Thus, $\log_{10} b > \log_{10}(\alpha^{n-1}) = (n-1)\log_{10} \alpha \approx (n-1)0.208 > (n-1)/5$.
+     - If $b$ has $k$ decimal digits, then $\log_{10} b < k$, so $n-1 < 5k$, so $n \le 5k$.