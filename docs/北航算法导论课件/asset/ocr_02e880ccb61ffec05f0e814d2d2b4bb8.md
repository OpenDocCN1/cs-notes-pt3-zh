# Step 2: A recursive solution

A₁ A₂ A₃ A₄ A₅: (A₁ A₂ A₃)(A₄ A₅)?   (A₁ A₂)(A₃ A₄ A₅)? ……
    A₁(A₂ A₃)?   (A₁ A₂)A₃?

m[i,j]=m[i,k]+m[k+1,j]+p_{i-1}p_kp_j

+   - This recursive equation assumes that we know the value of k, which we actually do not know. （递归方程假设已知矩阵连乘最佳全括号问题的分隔点 k，实际上 k 是未知的。）

+   - Only j-i possible values for k, namely k=i, i+1, ..., j-1.

+   - The optimal parenthesization must use one of these values for k. Checking them all to find the best, we have
+   （最佳全括号中必定使用 {i, i+1, ..., j-1} 中的一个值作为 k）

m[i, j] = { 0 , if i = j,
 min_{i ≤ k < j} { m[i, k] + m[k + 1, j] + p_{i-1} p_k p_j }, if i < j. (15.12)

+   - The m[i,j] give the costs of optimal solutions to subproblems.