# Proof of Lamé’s Theorem

+   - Consider the sequence of division-algorithm equations used in Euclid’s alg.:
+     $r_0 = r_1 q_1 + r_2$ with $0 \le r_2 < r_1$
+     $r_1 = r_2 q_2 + r_3$ with $0 \le r_3 < r_2$
+     ...
+     $r_{n-2} = r_{n-1} q_{n-1} + r_n$ with $0 \le r_n < r_{n-1}$
+     $r_{n-1} = r_n q_n + r_{n+1}$ with $r_{n+1} = 0$ (terminate)
+   - The number of divisions (iterations) is $n$.

Where $a = r_0$, $b = r_1$, and $\gcd(a,b)=r_n$.

Continued on next slide...