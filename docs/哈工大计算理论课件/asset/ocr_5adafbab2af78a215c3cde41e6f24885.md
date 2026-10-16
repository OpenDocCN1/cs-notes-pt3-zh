# Reductions via computation histories

+   - First, $B$ breaks up $x$ according to the delimiters into strings $C_1$, $C_2$,..., $C_l$. Then B determines whether the $C_i$ satisfy the three conditions of an accepting computation history.
+     - $C_1$ is the start configuration of $M$ on $w$,
+     - each $C_{i+1}$ legally follows from $C_i$ according to the rules of $M$,
+     - $C_l$ is an accepting configuration of $M$.