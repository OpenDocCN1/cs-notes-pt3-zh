# Recursion theorem

+   - $B = $ “On input $w$:
+     1. Obtain, via the recursion theorem, own description $\langle B\rangle$.
+     2. Run $H$ on input $\langle B,w\rangle$.
+     3. Do the opposite of what $H$ says: *accept* if $H$ rejects and *reject* if $H$ accepts.”
+   - On $w$ we can see the contradiction of $B$ and $H$. So $H$ cannot be deciding $A_{\text{TM}}$. So $A_{\text{TM}}$ is undecidable.