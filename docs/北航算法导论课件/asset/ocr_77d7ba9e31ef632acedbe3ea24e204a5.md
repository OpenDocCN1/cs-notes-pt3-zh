# Step 3: Computing the optimal costs

![](bbox=[0.145, 0.124, 0.872, 0.263])

$$m[i,j]=\begin{cases}0,&\text{if }i=j,\\\min_{i\le k<j}\{m[i,k]+m[k+1,j]+p_{i-1}p_kp_j\},&\text{if }i<j.\end{cases}$$ (15.12)

$A_i$: dimensions $p_{i-1}\times p_i$

**Input:** $p=\langle p_0,p_1,\ldots,p_n\rangle$.

# Procedure:

Table $m[1..n,1..n]$ storing the $m[i,j]$ costs;

Auxiliary table $s[1..n,1..n]$ recording which index of $k$ achieved the optimal cost in computing $m[i,j]$.

（计算 $m[i,j]$ 时，用辅助表项 (table entry) $s[i,j]$ 来记录最佳位置 $k$ 的值）

```
```text
MATRIX-CHAIN-ORDER(p)
1  n ← length[p] − 1
2  for i ← 1 to n
3      m[i, i] ← 0
4  for l ← 2 to n              // l is the chain length.
5      for i ← 1 to n − l + 1
6          j ← i + l − 1
7          m[i, j] ← ∞
8          for k ← i to j − 1
9              q ← m[i, k] + m[k + 1, j] + pᵢ₋₁pₖpⱼ
10             if q < m[i, j]
11                 m[i, j] ← q
12                 s[i, j] ← k
13 return m and s
```
```