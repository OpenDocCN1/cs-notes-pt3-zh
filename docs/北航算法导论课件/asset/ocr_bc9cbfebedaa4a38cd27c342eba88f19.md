# Step 3: Computing the optimal costs

m[i, j] = { 0 , if i = j, min_{i ≤ k < j} { m[i, k] + m[k + 1, j] + p_{i-1} p_k p_j }, if i < j. (15.12)

A₁ 30×35
A₂ 35×15
A₃ 15×5
A₄ 5×10
A₅ 10×20
A₆ 20×25

```
MATRIX-CHAIN-ORDER(p)
1 n ← length[p] − 1
2 for i ← 1 to n
3   m[i, i] ← 0
4 for l ← 2 to n    // l is the chain length.
5   for i ← 1 to n − l + 1
6     j ← i + l − 1
7     m[i, j] ← ∞
8     for k ← i to j − 1
9       q ← m[i, k] + m[k + 1, j] + p_{i-1} p_k p_j
10      if q < m[i, j]
11        m[i, j] ← q
12        s[i, j] ← k
13 return m and s
```

![](bbox=[0.6, 0.35, 0.95, 0.7])

![](bbox=[0.65, 0.75, 0.95, 0.95])