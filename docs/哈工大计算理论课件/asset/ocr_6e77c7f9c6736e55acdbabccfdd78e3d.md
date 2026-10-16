# Exponential Space Completeness

+   - Proof of is $EQ_{REX} \uparrow$ EXPSPACE-hard:
+     - Let $A$ be a language that is decided by TM $M$ running in space $2^{(n^k)}$ for some constant $k$
+     - The reduction maps an input $w$ to a pair of regular expressions, $R_1$ and $R_2$
+     - Expression $R_1$ is $\Delta^*$
+       - where $\Delta = (M\text{'s tape alphabet}) \cup (states) \cup \{#\}$ is the alphabet consisting of all symbols that may appear in a computation history
+     - Expression $R_2$ generates all strings that are not rejecting computation histories
+     - $M$ accepts $w$ iff $M$ on $w$ has no rejecting computation history, so the two expressions are equivalent iff $M$ accepts $w$