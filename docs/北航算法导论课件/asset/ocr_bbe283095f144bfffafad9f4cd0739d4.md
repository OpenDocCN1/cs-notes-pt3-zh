# Step 1: Characterizing an LCS

Theorem 15.1: (Optimal substructure of an LCS)

Let $Z=\langle z_1,\ldots,z_{k-1},z_k\rangle$ be any LCS of $X=\langle x_1,x_2,\ldots,x_m\rangle$ and $Y=\langle y_1,y_2,\ldots,y_n\rangle$.

+   1. If $x_m=y_n$, then $z_k=x_m=y_n$, and $Z_{k-1}$ is an LCS of $X_{m-1}$ and $Y_{n-1}$.
+   2. If $x_m\ne y_n$, then $z_k\ne x_m\Rightarrow Z$ is an LCS of $X_{m-1}$ and $Y$.
+   3. If $x_m\ne y_n$, then $z_k\ne y_n\Rightarrow Z$ is an LCS of $X$ and $Y_{n-1}$.

+   - Theorem 15.1 shows that **an LCS of two sequences contains within it an LCS of prefixes of the two sequences.**
+   
+     （两个序列的 an LCS 包含了这两个序列的前缀的 an LCS）
+   - the LCS problem has an optimal-substructure property.