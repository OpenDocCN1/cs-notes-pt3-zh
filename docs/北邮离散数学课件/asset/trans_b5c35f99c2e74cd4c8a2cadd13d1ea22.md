

# 集合差 - 维恩图

- *A−B* 是 *B* 在 *A* 上“咬了一口”后剩下的部分

![](img/c25dfd82fc242c2db53bc942dcad6885_2088_0.png)

# 集合补集

- *论域* 本身也可以被视为一个集合，记作 $U$。
- 当上下文明确定义了 $U$ 时，我们说对于任意集合 $A \subseteq U$，$A$ 的 *补集*，记作 $\overline{A}$，是 $A$ 关于 $U$ 的补集，即为 $U - A$。
- *例如*，若 $U = \mathbf{N}$，$\overline{\{3,5\}} = \{0,1,2,4,6,7,...\}$

# 关于集合补集的更多内容

- 当 $U$ 明确时，等价的定义为：

$\overline{A} = \{x \mid x \notin A\}$

![](img/c25dfd82fc242c2db53bc942dcad6885_2090_0.png)

![](img/c25dfd82fc242c2db53bc942dcad6885_2090_1.png)

# 集合恒等式

- 恒等式：$A \cup \varnothing = A = A \cap U$
- 支配律：$A \cup U = U$，$A \cap \varnothing = \varnothing$
- 幂等律：$A \cup A = A = A \cap A$
- 双重补集：$\overline{(\overline{A})} = A$
- 交换律：$A \cup B = B \cup A$，$A \cap B = B \cap A$
- 结合律：$A \cup (B \cup C) = (A \cup B) \cup C$，$A \cap (B \cap C) = (A \cap B) \cap C$

# 集合的德摩根律

- 与命题的德摩根律完全类似，且可由其证明。

$\overline{A \cup B} = \overline{A} \cap \overline{B}$

$\overline{A \cap B} = \overline{A} \cup \overline{B}$

# 证明集合恒等式

要证明形如 $E_1 = E_2$ 的集合命题，其中 $E$ 为集合表达式，这里有三种有用的技巧：

- 1. 分别证明 $E_1 \subseteq E_2$ 且 $E_2 \subseteq E_1$。
- 2. 使用集合构造符号和逻辑等价。
- 3. 使用 *成员表*。

# 方法 1：互为子集

例：证明 $A \cap (B \cup C) = (A \cap B) \cup (A \cap C)$。

- 第 1 部分：证明 $A \cap (B \cup C) \subseteq (A \cap B) \cup (A \cap C)$。
  - 假设 $x \in A \cap (B \cup C)$，并证明 $x \in (A \cap B) \cup (A \cap C)$。
  - 我们知道 $x \in A$，且 $x \in B$ 或 $x \in C$。
    - 情况 1：$x \in B$。则 $x \in A \cap B$，所以 $x \in (A \cap B) \cup (A \cap C)$。
    - 情况 2：$x \in C$。则 $x \in A \cap C$，所以 $x \in (A \cap B) \cup (A \cap C)$。
  - 因此，$x \in (A \cap B) \cup (A \cap C)$。
  - 因此，$A \cap (B \cup C) \subseteq (A \cap B) \cup (A \cap C)$。

- 第 2 部分：证明 $(A \cap B) \cup (A \cap C) \subseteq A \cap (B \cup C)$。...

# 方法 3：成员表

- 就像命题逻辑的真值表一样。
- 列用于不同的集合表达式。
- 行用于构成集合成员关系的全部组合。
- 用“1”表示属于导出集合，用“0”表示不属于。
- 通过列相同来证明等价。

# 成员表示例

证明 $(A \cup B)-B = A-B.$

| A | B | $A \cup B$ | $(A \cup B)-B$ | $A-B$ |
|---|---|---|---|---|
| 0 | 0 | 0 | 0 | 0 |
| 0 | 1 | 1 | 0 | 0 |
| 1 | 0 | 1 | 1 | 1 |
| 1 | 1 | 1 | 0 | 0 |

# 成员表练习

证明 $(A \cup B) - C = (A - C) \cup (B - C).$

| A | B | C | $A \cup B$ | $(A \cup B) - C$ | $A - C$ | $B - C$ | $(A - C) \cup (B - C)$ |
|---|---|---|------------|---------------|--------|--------|----------------------|
| 0 | 0 | 0 |  |  |  |  |  |
| 0 | 0 | 1 |  |  |  |  |  |
| 0 | 1 | 0 |  |  |  |  |  |
| 0 | 1 | 1 |  |  |  |  |  |
| 1 | 0 | 0 |  |  |  |  |  |
| 1 | 0 | 1 |  |  |  |  |  |
| 1 | 1 | 0 |  |  |  |  |  |
| 1 | 1 | 1 |  |  |  |  |  |

# § 2.1-2.2 回顾

- 集合 $S$，$T$，$U$... 特殊集合 **N**，**Z**，**R**。
- 集合记法 {a,b,...}，{x|P(x)}...
- 关系 $x \in S$，$S \subseteq T$，$S \supseteq T$，$S=T$，$S \subset T$，$S \supset T$。
- 运算 $|S|$，P(S)，$\times$，$\cup$，$\cap$，$\overline{S}$
- 集合相等证明技巧：$\stackrel{?}{S}$
  - 互为子集。
  - 使用逻辑等价进行推导。

# 广义并集与交集

- 由于并集与交集是可交换且可结合的，我们可以将它们从作用于集合的有序对 $(A,B)$ 扩展到作用于集合序列 $(A_1,...,A_n)$，甚至扩展到无序的 *集合* 的集合，$X=\{A \mid P(A)\}$。

