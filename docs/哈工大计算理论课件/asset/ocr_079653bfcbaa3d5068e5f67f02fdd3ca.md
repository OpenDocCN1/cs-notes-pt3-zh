# Complexity relationship among models

+   - Proof:
+   - Let $N$ be a nondeterministic TM running in $t(n)$ time. Construct a deterministic TM $D$ that simulates $N$ by searching $N$'s nondeterministic computation tree.
+   - Every branch of $N$'s nondeterministic computation tree has a length of at most $t(n)$. Let $b$ be the maximum number of legal choice given by $N$'s transition function. So every node in the tree can have at most $b$ children, and the total number of leaves in the tree is at most $b^{t(n)}$.