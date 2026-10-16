![](bbox=[0.0, 0.0, 0.074, 0.12])

# Example of Nesting

+   - Rewrite transaction $T_1$ using subtransactions $T_a$ and $T_b$ that perform increment or decrement operations:
+     - $T_1$ consists of
+       - $T_{1,1}$, which subtracts 50 from $A$
+       - $T_{1,2}$, which adds 50 to $B$

+   - Rewrite transaction $T_2$ using subtransactions $T_c$ and $T_d$ that perform increment or decrement operations:
+     - $T_2$ consists of
+       - $T_{2,1}$, which subtracts 10 from $B$
+       - $T_{2,2}$, which adds 10 to $A$

+   - No ordering is specified on subtransactions; any execution generates a correct result.