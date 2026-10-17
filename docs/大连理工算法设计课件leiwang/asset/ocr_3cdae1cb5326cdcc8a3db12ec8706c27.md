# # Lower bound for decision-tree sorting

**Theorem.** Any decision tree that can sort \( n \) elements must have height \( \Omega(n \lg n) \).

**Proof.** The tree must contain \( \ge n! \) leaves, since there are \( n! \) possible permutations. A height-\( h \) binary tree has \( \le 2^h \) leaves. Thus, \( n! \le 2^h \).

+   \(\therefore \ h \ge \lg(n!)\) (lg is mono. increasing)
+   \(\ge \lg \left((n/e)^n\right)\) (Stirling's formula)
+   \(= n \lg n - n \lg e\)
+   \(= \Omega(n \lg n)\).