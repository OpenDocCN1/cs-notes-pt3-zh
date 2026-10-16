

## 16.1.3 将DP解转化为贪心解

- **子问题是什么？**
  - 原问题是 $S_{0,n+1}$
  - 假设我们的第一个选择是 $a_{m_1}$
  - 那么下一个子问题是 $S_{m_1,n+1}$
  - 假设下一个选择是 $a_{m_2}$
  - 下一个子问题是 $S_{m_2,n+1}$
  - 以此类推

- 每个子问题都是 $S_{m_i,n+1}$。

- 并且所选的子问题，其完成时间是递增的。（所选的子问题，其完成时间是增序排列）

- 因此，我们可以按完成时间单调递增的顺序，对每个活动**只考虑一次**。

## 16.1.4 递归贪心算法

- 原问题是 $S_{0,n+1}$
- 每个子问题是 $S_{m_i,n+1}$
- 假设活动已经按完成时间单调递增的顺序排好序。（如果没有，则用 $O(n\lg n)$ 时间排序。）返回 $S_{i,n+1}$ 的一个最优解：

```
REC-ACTIVITY-SELECTOR(s, f, i, n)
1  m ← i+1 // initially i = 0, m = 1
2  while m≤n and sₘ < fᵢ  // Find first activity in Sᵢ,ₙ₊₁
3      m ← m+1
4  if m≤n
5      return {aₘ} ∪ REC-ACTIVITY-SELECTOR(s, f, m, n)
6  else return ∅
```

![](img/09c68ab421cfce4995ddad1430ef2637_440_0.png)

```
REC-ACTIVITY-SELECTOR(s, f, i, n)
1 m ← i+1
2 while m ≤ n and s_m < f_i  // Find first activity in S_{i,n+1}.
3     m ← m+1
4 if m ≤ n
5     return {a_m} ∪ REC-ACTIVITY-SELECTOR(s, f, m, n)
6 else return ∅
```

- *初始调用：* REC-ACTIVITY-SELECTOR(s, f, 0, n)。

- *思想：* while 循环检查 a_{i+1}, a_{i+2}, . . . , a_n，直到找到与 a_i 兼容的活动 a_m（需要 s_m ≥ f_i）。

- 如果循环因找到 a_m 而终止（m ≤ n），则递归求解 S_{m,n+1}，并将该解与 a_m 一起返回。

- 如果循环始终找不到兼容的 a_m（m > n），则直接返回空集。

![](img/09c68ab421cfce4995ddad1430ef2637_441_0.png)

![](img/09c68ab421cfce4995ddad1430ef2637_441_1.png)

```
REC-ACTIVITY-SELECTOR(s, f, i, n)
1 m ← i+1
2 while m ≤ n and s_m < f_i  // Find first activity in S_{i,n+1}.
3     m ← m+1
4 if m ≤ n
5     return {a_m} ∪ REC-ACTIVITY-SELECTOR(s, f, m, n)
6 else return ∅
```

- 时间：Θ(n)——每个活动恰好被检查一次。

T(n) = m₁ + T(n − m₁) = m₁ + m₂ + T(n − m₁ − m₂)
    = m₁ + m₂ + m₃ + T(n − m₁ − m₂ − m₃) = …
    = Σ m_k + T(n − Σ m_k)

基本情况：n − Σ m_k = 1，则 Σ m_k = n − 1，Σ m_k + T(1) = Θ(n)

- 初始调用：REC-ACTIVITY-SELECTOR(s, f, 0, n)。

- 思想：while 循环检查 a_{i+1}, a_{i+2}, ..., a_n，直到找到与 a_i 兼容的活动 a_m（需要 s_m ≥ f_i）。

- 如果循环因找到 a_m 而终止（m ≤ n），则递归求解 S_{m,n+1}，并将该解与 a_m 一起返回。

- 如果循环始终找不到兼容的 a_m（m > n），则直接返回空集。

![](img/09c68ab421cfce4995ddad1430ef2637_443_0.png)

## 16.1.5 迭代贪心算法

- **REC-ACTIVITY-SELECTOR 几乎是“尾递归”的。**
- **我们可以很容易地将递归过程转换为迭代过程。（有些编译器会自动执行此转换。）**

![](img/09c68ab421cfce4995ddad1430ef2637_444_0.png)

```
GREEDY-ACTIVITY-SELECTOR(s, f, n)
1  A ← {a₁}
2  i ← 1
3  for m ← 2 to n
4      if sₘ ≥ fᵢ
5          A ← A ∪ {aₘ}
6          i ← m   // aᵢ is most recent addition to A
7  return A
```

## 回顾

- **贪心算法思想：** 当我们面临选择时，选择 *当前* 看起来最好的那个。做出一个 *局部最优选择*，希望能得到 *全局最优解*。
  （希望当前选择是最好的，每一个局部最优选择能产生全局最优选择）
- **贪心算法：** 更简单，更高效

## 16 贪心算法

- 16.1，活动选择问题（活动安排）
- 16.2，贪心算法的基本要素；背包问题（贪婪算法的基本特征；背包问题）
- 16.3，一个重要应用：设计数据压缩（哈夫曼）编码（哈夫曼编码）

## 16.2 贪心策略的要素

- **选择当前看起来最好的那个**
  - （每次决策时，当前所做的选择看起来是“最好”的）
- **我们是如何解决活动选择问题的？**
  1. 确定最优子结构。
  2. 提出一个递归解。
  3. 证明在递归的任一阶段，最优选择之一就是贪心选择。
  4. 证明由贪心选择产生的子问题中，**除了一个之外，其余都是空**。（通过贪婪选择，只有一个子问题非空）
  5. 设计一个递归贪心算法。
  6. 将其转换为迭代算法。

