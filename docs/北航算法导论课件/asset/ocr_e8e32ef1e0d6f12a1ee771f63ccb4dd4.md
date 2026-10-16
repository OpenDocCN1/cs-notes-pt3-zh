# 15.3.3 Reconstructing an optimal solution

A₁ A₂ A₃ A₄ A₅ A₆

![](bbox=[0.38, 0.2, 0.75, 0.55])

![](bbox=[0.7, 0.1, 0.98, 0.55])

+   Storing choice is important.

+   Matrix-chain multiplication

+   Table s[i,j] saves a significant amount of work.

+   Suppose that we did not maintain table s[i,j], having filled in only the table m[i,j] containing optimal subproblem costs. There are j-i choices in determining which subproblems to use in an optimal solution to parenthesizing A_i A_{i+1} ... A_j, and j-i is not a constant. Therefore, it would take Θ(j-i) = ω(1) time to reconstruct which subproblems we chose for a solution to a given problem. (假设仅填写了包含最优值的表 m[i,j]，而没有填写表 s[i,j]，在最优问题中要确定使用哪一个子问题，需要从 j-i 选项中选择其一，而 j-i 不是常数，……)

```
m[i, j] = { 0, if i = j, min_{i ≤ k < j} [m[i,k] + m[k+1,j] + p_{i-1} p_k p_j], if i < j. }
```