

## Step 1: 刻画一个 LCS

X = <x₁, x₂, ..., xₘ> 和 Y = <y₁, y₂, ..., yₙ>

- LCS 问题具有 **最优子结构** 属性。
  （LCS问题具有最优子结构属性）

- 子问题的自然分类：前缀
  （子问题的自然分类：前缀）
  Xᵢ = <x₁, ..., xᵢ>，X 的第 i 个前缀，i = 0, 1, ..., m
  Yⱼ = <y₁, ..., yⱼ>，Y 的第 j 个前缀，j = 0, 1, ..., n

例如，如果 X = <A, B, C, B, D, A, B>，则 X₄ = <A, B, C, B>，且 X₀ 是空序列。

## Step 1: 刻画一个 LCS

定理 15.1：(LCS 的最优子结构)
设 Z = < z₁, ..., zₖ₋₁ , zₖ > 是
X = < x₁, ..., xₘ₋₁ , xₘ >
和 Y = < y₁, ..., yₙ₋₁ , yₙ > 的任意 LCS。
（设 Z 是 X 和 Y 的任意 LCS）

1. 如果 xₘ = yₙ，则 zₖ = xₘ = yₙ 且 Zₖ₋₁ 是 Xₘ₋₁ 和 Yₙ₋₁ 的一个 LCS。
2. 如果 xₘ ≠ yₙ，则 zₖ ≠ xₘ ⇒ Z 是 Xₘ₋₁ 和 Y 的一个 LCS。
3. 如果 xₘ ≠ yₙ，则 zₖ ≠ yₙ ⇒ Z 是 X 和 Yₙ₋₁ 的一个 LCS。

## Step 1: 刻画一个 LCS

![](img/09c68ab421cfce4995ddad1430ef2637_403_0.png)

□ **定理 15.1: (LCS 的最优子结构)**  
设 $Z=\langle z_1,\ldots,z_k\rangle$ 是 $X=\langle x_1,\ldots,x_m\rangle$ 和 $Y=\langle y_1,\ldots,y_n\rangle$ 的任意 LCS。

- 2. 如果 $x_m\ne y_n$，则 $z_k\ne x_m \Rightarrow Z$ 是 $X_{m-1}$ 和 $Y$ 的一个 LCS。
- 3. 如果 $x_m\ne y_n$，则 $z_k\ne y_n \Rightarrow Z$ 是 $X$ 和 $Y_{n-1}$ 的一个 LCS。

### Proof:

2. 如果 $z_k\ne x_m$，则 $Z$ 是 $X_{m-1}$ 和 $Y$ 的一个 CS。设存在 $X_{m-1}$ 和 $Y$ 的一个子序列 $W$ 使得 length$(W)>k$。则 $W$ 是 $X$ 和 $Y$ 的一个 CS ⇒ 与 $Z$ 是 LCS 的假设矛盾。

（若$z_k\ne x_m$，则$Z$是$X_{m-1}$和$Y$的一个CS。设存在一个$X_{m-1}$和$Y$的子序列$W$，其length$(W)>k$，那么，$W$是$X$和$Y$的一个CS ⇒ 与题设$Z$是一个LCS矛盾）

3. 与 2 对称。

## Step 1: 刻画一个 LCS

定理 15.1：(LCS 的最优子结构)

设 $Z=\langle z_1,\ldots,z_{k-1},z_k\rangle$ 是 $X=\langle x_1,x_2,\ldots,x_m\rangle$ 和 $Y=\langle y_1,y_2,\ldots,y_n\rangle$ 的任意 LCS。

- 1. 如果 $x_m=y_n$，则 $z_k=x_m=y_n$，且 $Z_{k-1}$ 是 $X_{m-1}$ 和 $Y_{n-1}$ 的一个 LCS。
- 2. 如果 $x_m\ne y_n$，则 $z_k\ne x_m\Rightarrow Z$ 是 $X_{m-1}$ 和 $Y$ 的一个 LCS。
- 3. 如果 $x_m\ne y_n$，则 $z_k\ne y_n\Rightarrow Z$ 是 $X$ 和 $Y_{n-1}$ 的一个 LCS。

- 定理 15.1 表明 **两个序列的一个 LCS 包含了这两个序列的前缀的一个 LCS。**
  
  （两个序列的 an LCS 包含了这两个序列的前缀的 an LCS）
- LCS 问题具有最优子结构属性。

## Step 1: 刻画一个 LCS

- 最优子结构属性：定理 15.1 表明一个 LCS 包含了这两个序列的前缀的一个 LCS。
  （两个序列的 an LCS 包含了这两个序列的前缀的 an LCS）
- 例如

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

## Step 2: 一个递归解法

- 定理 15.1 意味着在寻找 X 和 Y 的 LCS 时，有一个或两个子问题需要检查。
  （当求 an LCS时，定理表明了有一个或两个子问题需要考虑）
- 设 c[i,j] 为 X_i 和 Y_j 的一个 LCS 的长度 (c[i,j]=0, i,j=0)。

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

## Step 2: 一个递归解法

LCS 问题的最优子结构给出了递归公式。 （由LCS问题的最优子结构可导出递归公式）

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

