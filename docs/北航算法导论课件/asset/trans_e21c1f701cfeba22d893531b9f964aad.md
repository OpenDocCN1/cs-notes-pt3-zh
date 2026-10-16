

## Step 2: 递归解法

- 子问题：寻找包含键 $k_i$, ..., $k_j$ 的最优 BST，其中 $i \ge 1$, $j \le n$, 且 $j \ge i-1$。 （当 $j=i-1$ 时，没有实际键，只有虚拟键 $d_{i-1}$。）
- $e[i,j]$：包含键 $k_i$, ..., $k_j$ 的最优 BST 的期望搜索代价。
- 最终，希望计算 $e[1, n]$。
- 当 $j=i-1$ 时，只有 $d_{i-1}$，$e[i, i-1] = q_{i-1}$。
- 当 $j \ge i$ 时？

![](img/09c68ab421cfce4995ddad1430ef2637_314_0.png)

![](img/09c68ab421cfce4995ddad1430ef2637_314_1.png)

- 当 $j \ge i$ 时，从 $k_i$, ..., $k_j$ 中选择一个根 $k_r$，然后使包含键 $k_i$, ..., $k_{r-1}$ 的最优 BST 作为其左子树，包含键 $k_{r+1}$, ..., $k_j$ 的最优 BST 作为其右子树。

![](img/09c68ab421cfce4995ddad1430ef2637_315_0.png)

![](img/09c68ab421cfce4995ddad1430ef2637_315_1.png)

- 当一个子树成为某个节点的子树时，其期望搜索代价会发生什么？

- 子树中每个节点的深度增加 1，该子树的期望搜索代价增加该子树中所有概率之和。 （子树中每个节点的深度增加 1，该子树的期望搜索的 cost 的增量为该子树所有节点的搜索概率之和，...) 概率之和：

增量: $w[i, j] = \sum_{i=i}^{j} p_i + \sum_{i=i-1}^{j} q_i \quad (15.17)$

![](img/09c68ab421cfce4995ddad1430ef2637_316_0.png)

E_T = e[m, n]

![](img/09c68ab421cfce4995ddad1430ef2637_316_1.png)

E_T = \sum_{x=m}^{n} (depth(k_x)+1+1)·p_x + \sum_{x=m-1}^{n} (depth(d_x)+1+1)·q_x

= \sum_{x=m}^{n} (depth(k_x)+1)·p_x + \sum_{x=m-1}^{n} (depth(d_x)+1)·q_x + \sum_{x=m}^{n} p_i + \sum_{x=m}^{n} q_x

= e[m, n] + w[m, n]

- 因此，如果 $k_r$ 是包含键 $k_i$, ..., $k_j$ 的最优子树的根，我们有
- $e[i,j] = p_r + (e[i, r-1] + w[i, r-1])$
- $+ (e[r+1,j] + w[r+1,j])$ ?

![](img/09c68ab421cfce4995ddad1430ef2637_317_0.png)

注意到 $w[i,j] = w[i, r-1] + p_r + w[r+1,j]$

$\left( w[i, r-1] = \sum_{l=i}^{r-1} p_l + \sum_{l=i-1}^{r-1} q_l \quad , \quad w[r+1, j] = \sum_{l=r+1}^{j} p_l + \sum_{l=r}^{j} q_l \right)$

我们重写 $e[i,j]$ 为

$e[i,j] = e[i, r-1] + e[r+1,j] + w[i,j] \quad (15.18)$

递归方程 (15.18) 假设我们知道要用作根的节点 $k_r$，而我们并不知道。

![](img/09c68ab421cfce4995ddad1430ef2637_318_0.png)

- 选择使期望搜索代价最低的 $k_r$ 作为根，给出我们的最终递归公式：
- 
$$e[i,j] = \begin{cases} q_{i-1}, & \text{if } j=i-1, \\ \displaystyle\min_{i\le r\le j}\{e[i,r-1]+e[r+1,j]+w[i,j]\}, & \text{if } i\le j. \end{cases} \tag{15.19}$$

- $e[i,j]$ 给出最优 BST 中的期望搜索代价。

- 为了帮助我们跟踪最优 BST 的结构，定义 $root[i,j]$，对于 $1\le i\le j\le n$，为使 $k_r$ 成为包含键 $k_i,\ldots,k_j$ 的最优 BST 的根的索引 $r$。

## Step 3: 计算期望搜索代价

A_i ... A_r ... A_j

![](img/09c68ab421cfce4995ddad1430ef2637_319_0.png)

![](img/09c68ab421cfce4995ddad1430ef2637_319_1.png)

```
e[i, j] = { q_{i-1} if j = i-1, min_{i ≤ r ≤ j} { e[i, r-1] + e[r+1, j] + w[i, j] } if i ≤ j. (15.19)
```

- 相似性：最优 BST 和矩阵链乘法。

- 直接的递归实现会非常低效。

- 将 $e[i,j]$ 值存储在表 $e[1.. n+1, 0.. n]$ 中。

  - 第一个索引运行到 $n+1$，为了拥有仅包含 $d_n$ 的子树，需要计算并存储 $e[n+1, n]$。

  - 第二个索引从 0 开始，为了拥有仅包含 $d_0$ 的子树，需要计算并存储 $e[1, 0]$。

- 使用表 $root[i,j]$，用于记录包含键 $k_i$, ..., $k_j$ 的子树的根，仅用于 $1 \le i \le j \le n$。

- 为效率而设的其他表。
- $e[i,j] = e[i,r-1] + e[r+1,j] + w[i,j]$  (15.18)
- 而不是每次计算 $e[i,j]$ 时都计算 $w[i,j]$ 的值——这将花费 $\Theta(j-i)$ 次加法——我们将这些值存储在表 $w[1..n+1, 0..n]$ 中。
- （无需每次计算 $e[i,j]$ 时都计算 $w[i,j]$，...）
- 对于基本情况，我们计算 $w[i,i-1] = q_{i-1}$ 对于 $1\le i\le n$。
- 对于 $j\ge i$，$w[i,j] = \sum_{l=i}^{j} p_l + \sum_{l=i-1}^{j} q_l = w[i,j-1] + p_j + q_j$  (15.20)
- 因此，以每个 $\Theta(1)$ 时间计算 $\Theta(n^2)$ 个 $w[i,j]$ 值。
- 输入：概率 $p_1, ..., p_n$ 和 $q_0, ..., q_n$ 以及大小 $n$

