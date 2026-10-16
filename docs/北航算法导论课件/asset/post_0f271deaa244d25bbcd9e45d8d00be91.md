
## Step 1: Characterizing an LCS

X = <x₁, x₂, ..., xₘ> and Y = <y₁, y₂, ..., yₙ>

- The LCS problem has an **optimal-substructure** property.
  （LCS问题具有最优子结构属性）

- Natural classes of subproblems: prefixes
  （子问题的自然分类：前缀）
  Xᵢ = <x₁, ..., xᵢ>, the i-th prefix of X, for i = 0, 1, ..., m
  Yⱼ = <y₁, ..., yⱼ>, the j-th prefix of Y, for j = 0, 1, ..., n

For example, if X = <A, B, C, B, D, A, B>, then X₄ = <A, B, C, B>, and X₀ is the empty sequence.

## Step 1: Characterizing an LCS

Theorem 15.1: (Optimal substructure of an LCS)
Let Z = < z₁, ..., zₖ₋₁ , zₖ > be any LCS of
X = < x₁, ..., xₘ₋₁ , xₘ >
and Y = < y₁, ..., yₙ₋₁ , yₙ >.
（设 Z 是 X 和 Y 的任意 LCS）

1. If xₘ = yₙ, then zₖ = xₘ = yₙ and Zₖ₋₁ is an LCS of Xₘ₋₁ and Yₙ₋₁.
2. If xₘ ≠ yₙ, then zₖ ≠ xₘ ⇒ Z is an LCS of Xₘ₋₁ and Y.
3. If xₘ ≠ yₙ, then zₖ ≠ yₙ ⇒ Z is an LCS of X and Yₙ₋₁.

## Step 1: Characterizing an LCS

![](img/09c68ab421cfce4995ddad1430ef2637_403_0.png)

□ **Theorem 15.1: (Optimal substructure of an LCS)**  
Let $Z=\langle z_1,\ldots,z_k\rangle$ be any LCS of $X=\langle x_1,\ldots,x_m\rangle$ and $Y=\langle y_1,\ldots,y_n\rangle$.

- 2. If $x_m\ne y_n$, then $z_k\ne x_m \Rightarrow Z$ is an LCS of $X_{m-1}$ and $Y$.
- 3. If $x_m\ne y_n$, then $z_k\ne y_n \Rightarrow Z$ is an LCS of $X$ and $Y_{n-1}$.

### Proof:

2. If $z_k\ne x_m$, then $Z$ is a CS of $X_{m-1}$ and $Y$. Suppose there exists a subsequence $W$ of $X_{m-1}$ and $Y$ with length $>k$. Then $W$ is a CS of $X$ and $Y \Rightarrow$ contradicts $Z$ being an LCS.

（若$z_k\ne x_m$，则$Z$是$X_{m-1}$和$Y$的一个CS。设存在一个$X_{m-1}$和$Y$的子序列$W$，其length$(W)>k$，那么，$W$是$X$和$Y$的一个CS ⇒ 与题设$Z$是一个LCS矛盾）

3. Symmetric to 2.

## Step 1: Characterizing an LCS

Theorem 15.1: (Optimal substructure of an LCS)

Let $Z=\langle z_1,\ldots,z_{k-1},z_k\rangle$ be any LCS of $X=\langle x_1,x_2,\ldots,x_m\rangle$ and $Y=\langle y_1,y_2,\ldots,y_n\rangle$.

- 1. If $x_m=y_n$, then $z_k=x_m=y_n$, and $Z_{k-1}$ is an LCS of $X_{m-1}$ and $Y_{n-1}$.
- 2. If $x_m\ne y_n$, then $z_k\ne x_m\Rightarrow Z$ is an LCS of $X_{m-1}$ and $Y$.
- 3. If $x_m\ne y_n$, then $z_k\ne y_n\Rightarrow Z$ is an LCS of $X$ and $Y_{n-1}$.

- Theorem 15.1 shows that **an LCS of two sequences contains within it an LCS of prefixes of the two sequences.**
  
  （两个序列的 an LCS 包含了这两个序列的前缀的 an LCS）
- the LCS problem has an optimal-substructure property.

## Step 1: Characterizing an LCS

- Optimal-substructure property: Theorem 15.1 shows that an LCS of two sequences contains within it an LCS of prefixes of the two sequences.
  （两个序列的 an LCS 包含了这两个序列的前缀的 an LCS）
- For example

X = < x₁, x₂, ..., xₘ >
Z = < z₁, z₂, ..., zₖ >
Y = < y₁, y₂, ..., yₙ >

Xₘ₋₁ = < x₁, x₂, ..., xₘ₋₁ >
Zₖ₋₁ = < z₁, z₂, ..., zₖ₋₁ >
Yₙ₋₁ = < y₁, y₂, ..., yₙ₋₁ >

xₘ = yₙ

Xₘ₋₁ = < x₁, x₂, ..., xₘ₋₁ >
Z = < z₁, z₂, ..., zₖ >
Y = < y₁, y₂, ..., yₙ >

xₘ ≠ yₙ
zₖ ≠ xₘ

X = < x₁, x₂, ..., xₘ >
Z = < z₁, z₂, ..., zₖ >
Yₙ₋₁ = < y₁, y₂, ..., yₙ₋₁ >

xₘ ≠ yₙ
zₖ ≠ yₙ

## Step 2: A recursive solution

- Theorem 15.1 implies that there are either one or two subproblems to examine when finding an LCS of X and Y.
  （当求 an LCS时，定理表明了有一个或两个子问题需要考虑）
- Let c[i,j] be the length of an LCS of X_i and Y_j (c[i,j]=0, i,j=0).

X_i = <x_1, x_2, ..., x_i>
Z_k = <z_1, z_2, ..., z_k>
Y_j = <y_1, y_2, ..., y_j>

x_i = y_j

X_{i-1} = <x_1, x_2, ..., x_{i-1}>
Z_{k-1} = <z_1, z_2, ..., z_{k-1}>
Y_{j-1} = <y_1, y_2, ..., y_{j-1}>

c[i,j] = c[i-1,j-1] + 1

x_i ≠ y_j
z_k ≠ x_i

X_{i-1} = <x_1, x_2, ..., x_{i-1}>
Z_k = <z_1, z_2, ..., z_k>
Y_j = <y_1, y_2, ..., y_j>

c[i,j] = max( c[i-1,j], c[i,j-1] )

x_i ≠ y_j
z_k ≠ y_j

X_i = <x_1, x_2, ..., x_i>
Z_k = <z_1, z_2, ..., z_k>
Y_{j-1} = <y_1, y_2, ..., y_{j-1}>

## Step 2: A recursive solution

The optimal substructure of the LCS problem gives the recursive formula. （由LCS问题的最优子结构可导出递归公式）

X_i = < x_1, x_2, ..., x_i >
Z_k = < z_1, z_2, ..., z_k >
Y_j = < y_1, y_2, ..., y_j >

x_i = y_j

X_{i-1} = < x_1, x_2, ..., x_{i-1} >
Z_{k-1} = < z_1, z_2, ..., z_{k-1} >
Y_{j-1} = < y_1, y_2, ..., y_{j-1} >

c[i,j] = c[i-1,j-1] + 1

x_i ≠ y_j
z_k ≠ x_i

X_{i-1} = < x_1, x_2, ..., x_{i-1} >
Z_k = < z_1, z_2, ..., z_k >
Y_j = < y_1, y_2, ..., y_j >

c[i,j] = max( c[i-1,j], c[i,j-1] )

x_i ≠ y_j
z_k ≠ y_j

X_i = < x_1, x_2, ..., x_i >
Z_k = < z_1, z_2, ..., z_k >
Y_{j-1} = < y_1, y_2, ..., y_{j-1} >

c[i,j] = { 0 if i = 0 or j = 0,
 c[i-1, j-1] + 1, if i, j > 0 and x_i = y_j, (15.14)
 max( c[i-1, j], c[i, j-1] ), if i, j > 0 and x_i ≠ y_j. }
