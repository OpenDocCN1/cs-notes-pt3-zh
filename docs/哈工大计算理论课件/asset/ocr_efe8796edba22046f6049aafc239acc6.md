# Savitch’s Theorem

+   - Proof:
+     - Let $N$ be an NTM deciding a language $A$ in space $f(n)$
+     - Then, we construct a DTM $M$ to decide language $A$
+     - We use the procedures described in previous slide to build the procedure called CANYIELD
+     - Let $w$ be an input string of $N$ and it generates two configurations $c_1$ and $c_2$.
+     - CANYIELD$(c_1, c_2, t)$ outputs accept if $N$ can go from $c_1$ to $c_2$ within $t$ steps along some nondetereministic path