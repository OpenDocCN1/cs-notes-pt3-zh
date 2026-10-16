# Reductions via computation histories

+   - Instead of actually constructing $G$, we construct a PDA $D$, then we certainly can convert $D$ to $G$.
+   - As there are three conditions to test, so we have to design $D$ having three copies.
+     - One checks on whether the beginning of the input string is $C_1$.
+     - One checks on whether the input string ends with a configuration containing the accept state, $q_{accept}$.
+     - One checks on whether every $C_i$ properly yields $C_{i+1}$ under the rules of $M$