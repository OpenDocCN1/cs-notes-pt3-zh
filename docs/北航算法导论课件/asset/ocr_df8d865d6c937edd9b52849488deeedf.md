# Step 2: A recursive solution

+   - Subproblem : finding an optimal BST containing the keys $k_i$, ..., $k_j$, where $i \ge 1$, $j \le n$, and $j \ge i-1$. (when $j=i-1$, there are no actual keys, we have just the dummy key $d_{i-1}$.)
+   - $e[i,j]$ : the expected cost of searching an optimal BST containing the keys $k_i$, ..., $k_j$.
+   - Ultimately, wish to compute $e[1, n]$.
+   - when $j=i-1$, only $d_{i-1}$, $e[i, i-1] = q_{i-1}$.
+   - When $j \ge i$ ?

![](bbox=[0.24, 0.66, 0.56, 0.94])

![](bbox=[0.62, 0.45, 0.92, 0.78])