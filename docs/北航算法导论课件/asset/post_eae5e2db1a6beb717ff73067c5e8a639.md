
## Step 4: Constructing an optimal solution

```
PRINT-OPTIMAL-PARENS(s, i, j)
1 if i == j
2   print "A"_i
3 else
4   print "("
5   PRINT-OPTIMAL-PARENS(s, i, s[i, j])
6   PRINT-OPTIMAL-PARENS(s, s[i, j]+1, j)
7   print ")"
```

A₁ A₂ A₃ A₄ A₅ A₆: ((A₁ A₂ A₃) (A₄ A₅) A₆)? A₁ (A₂ A₃)?   (A₁ A₂) A₃?

- A₁ 30×35
- A₂ 35×15
- A₃ 15×5
- A₄ 5×10
- A₅ 10×20
- A₆ 20×25

![](img/09c68ab421cfce4995ddad1430ef2637_294_0.png)

```
s(1,6)

( s(1,3) s(4,6) )

( s(1,1) s(2,3) )

( s(2,2) s(3,3) )

((A₁(A₂ A₃)) ((A₄ A₅) A₆))
```

## Exercises

Use the substitution method to show that the solution to the recurrence (15.11) is $\Omega(2^n)$.

$$P(n)=\begin{cases}1, & \text{if } n=1,\\\displaystyle\sum_{k=1}^{n-1}P(k)P(n-k), & \text{if } n\ge 2.\end{cases}\tag{15.11}$$

### Solution

We need $P(n) \ge c \cdot 2^{n}$.

$P(k) \ge c \cdot 2^{k} \Rightarrow$

$P(n) = \sum_{k=1}^{n-1} P(k)P(n-k)$

$\ge \sum_{k=1}^{n-1} c \cdot 2^{k} \cdot c \cdot 2^{n-k} = \sum_{k=1}^{n-1} c^{2} \cdot 2^{n} = (n-1) \cdot c^{2} \cdot 2^{n}$

$\ge c \cdot 2^{n}$  ( if $(n-1) \cdot c^{2} \ge c$, that is $c \ge \dfrac{1}{n-1}$ )

## 15 Dynamic Programming

- Scheduling two automobile assembly lines
  - （流水线、装配线调度）
- Matrix-chain multiplication
  - （矩阵链相乘，或矩阵连乘问题）
- Characteristics of dynamic programming
  - （动态规划法的特征）
- Longest common subsequence （最长相同子序列）
- **Optimal binary search trees** （最优二叉搜索树）

### 15.5 Optimal binary search trees

- Design a program to translate text from English to Chinese
  （例如自动翻译机）

![](img/09c68ab421cfce4995ddad1430ef2637_298_0.png)

![](img/09c68ab421cfce4995ddad1430ef2637_298_1.png)

**生词表**

| 字段1 | 字段2 |
|---|---|
| aggregate analysis | 综合分析;总体分析 |
| amortized | *** |
| arbitrary | 任意的, 武断的, 独裁的, 专断的 |
| auxiliary | *** |
| binomial | 二项的, 二项式的 |
| bog | 沼泽, 陷于泥沼 |
| contemporary | 当代的, 同时代的 |
| convention | 归约, 常规 |
| crucial | 至关重要的 |
| disjoint | 不相交的,不相接的,分离的 |
| distinct | 清楚的, 明显的, 截然不同的, 独特的 |

### 15.5 Optimal binary search trees

- Need the total time spent searching to be as low as possible.
- Words appear with different frequencies.
- It may be: “algorithm” (frequently used) appears far from the root; “mycophagist” (rarely used, 食菌者) appears near the root.
- （高频出现的单词出现在远离树根的节点，......）
- Such an organization would slow down the translation, since # of nodes visited when searching for a key in a BST is “one plus the depth of the node containing the key” (1+depth).
- We want words that occur frequently in the text to be placed nearer the root.

![](img/09c68ab421cfce4995ddad1430ef2637_301_0.png)

### 15.5 Optimal binary search trees

- Given a sequence $K=\langle k_1,k_2,\ldots,k_n\rangle$ of $n$ distinct keys in sorted order $(k_1<k_2<\cdots<k_n)$, how to build a BST?
  - For each key $k_i$, search probability $p_i$ (it can also be the number $I$ of occurrence of $k_i$ in the text, whose number of total words is $M$, then $p_i=I/M$.)
  - Some values not in $K$, $n+1$ "dummy keys" $d_0,d_1,\ldots,d_n$
  - $d_0$ represents all values $<k_1$; $d_n$ represents all values $>k_n$
  - for $1\le i\le n-1$, $d_i$: $k_i<d_i<k_{i+1}$, search probability $q_i$
  - Fig: each key $k_i$, an internal node; $d_i$, a leaf

![](img/09c68ab421cfce4995ddad1430ef2637_303_0.png)

| $i$ | 0 | 1 | 2 | 3 | 4 | 5 |
|---|---:|---:|---:|---:|---:|---:|
| $p_i$ |  | 0.15 | 0.10 | 0.05 | 0.10 | 0.20 |
| $q_i$ | 0.05 | 0.10 | 0.05 | 0.05 | 0.05 | 0.10 |

### 15.5 Optimal binary search trees

- Every search is either successful or unsuccessful, we have

$$\sum_{i=1}^{n} p_i + \sum_{i=0}^{n} q_i = 1 \quad (15.15)$$

- We have probabilities of searches for each (dummy) key, we can determine the expected cost of a search in a given BST $T$.

- Assume that the actual cost of a search is the number of nodes examined. Then the expected cost of a search in $T$ is

$$\mathrm{E}[\text{search cost in } T]=\sum_{i=1}^{n}(\text{depth}_T(k_i)+1)\cdot p_i + \sum_{i=0}^{n}(\text{depth}_T(d_i)+1)\cdot q_i$$

$$=1+\sum_{i=1}^{n}\text{depth}_T(k_i)\cdot p_i + \sum_{i=0}^{n}\text{depth}_T(d_i)\cdot q_i, \quad (15.16)$$

where $\text{depth}_T$ denotes a node's depth in the tree $T$.
