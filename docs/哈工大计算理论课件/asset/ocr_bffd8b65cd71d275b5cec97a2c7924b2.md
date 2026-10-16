# The TQBF Problem

+   - Then, we analyze the space used by the new algorithm for the formula φ_{c_start, c_accept, h}, where h = 2^{d f(n)}
+     - At each level of recursion, we add a portion to the formula which is linear in the size of the configuration and thus the size is O(f(n))
+     - The number of levels of the recursion is log 2^{d f(n)}, or O(f(n))
+     - So, the total space used is O(f^2(n))