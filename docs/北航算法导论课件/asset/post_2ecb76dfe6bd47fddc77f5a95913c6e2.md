
## Step 2: A recursive solution

- Subproblem : finding an optimal BST containing the keys $k_i$, ..., $k_j$, where $i \ge 1$, $j \le n$, and $j \ge i-1$. (when $j=i-1$, there are no actual keys, we have just the dummy key $d_{i-1}$.)
- $e[i,j]$ : the expected cost of searching an optimal BST containing the keys $k_i$, ..., $k_j$.
- Ultimately, wish to compute $e[1, n]$.
- when $j=i-1$, only $d_{i-1}$, $e[i, i-1] = q_{i-1}$.
- When $j \ge i$ ?

![](img/09c68ab421cfce4995ddad1430ef2637_314_0.png)

![](img/09c68ab421cfce4995ddad1430ef2637_314_1.png)

- When j ≥ i, select a root k_r from among k_i , ..., k_j , and then make an optimal BST with keys k_i , ..., k_{r-1} its left subtree and an optimal BST with keys k_{r+1} , ..., k_j its right subtree.

![](img/09c68ab421cfce4995ddad1430ef2637_315_0.png)

![](img/09c68ab421cfce4995ddad1430ef2637_315_1.png)

- What happens to the expected search cost of a subtree when it becomes a subtree of a node?

- The depth of each node in the subtree increases by 1, the expected search cost of this subtree increases by the sum of all the probabilities in the subtree. (子树中每个节点的深度增加 1，该子树的期望搜索的 cost 的增量为该子树所有节点的搜索概率之和，...) the sum of probabilities:

增量: $w[i, j] = \sum_{i=i}^{j} p_i + \sum_{i=i-1}^{j} q_i \quad (15.17)$

![](img/09c68ab421cfce4995ddad1430ef2637_316_0.png)

E_T = e[m, n]

![](img/09c68ab421cfce4995ddad1430ef2637_316_1.png)

E_T = \sum_{x=m}^{n} (depth(k_x)+1+1)·p_x + \sum_{x=m-1}^{n} (depth(d_x)+1+1)·q_x

= \sum_{x=m}^{n} (depth(k_x)+1)·p_x + \sum_{x=m-1}^{n} (depth(d_x)+1)·q_x + \sum_{x=m}^{n} p_i + \sum_{x=m}^{n} q_x

= e[m, n] + w[m, n]

- Thus, if $k_r$ is the root of an optimal subtree containing keys $k_i$, ..., $k_j$, we have
- $e[i,j] = p_r + (e[i, r-1] + w[i, r-1])$
- $+ (e[r+1,j] + w[r+1,j])$ ?

![](img/09c68ab421cfce4995ddad1430ef2637_317_0.png)

Noting that $w[i,j] = w[i, r-1] + p_r + w[r+1,j]$

$\left( w[i, r-1] = \sum_{l=i}^{r-1} p_l + \sum_{l=i-1}^{r-1} q_l \quad , \quad w[r+1, j] = \sum_{l=r+1}^{j} p_l + \sum_{l=r}^{j} q_l \right)$

We rewrite $e[i,j]$ as

$e[i,j] = e[i, r-1] + e[r+1,j] + w[i,j] \quad (15.18)$

The recursive equation (15.18) assumes that we know which node $k_r$ to use as the root, which we do not know.

![](img/09c68ab421cfce4995ddad1430ef2637_318_0.png)

- Choose $k_r$ as the root that gives the lowest expected search cost, giving us our final recursive formulation:
- 
$$e[i,j] = \begin{cases} q_{i-1}, & \text{if } j=i-1, \\ \displaystyle\min_{i\le r\le j}\{e[i,r-1]+e[r+1,j]+w[i,j]\}, & \text{if } i\le j. \end{cases} \tag{15.19}$$

- $e[i,j]$ give the expected search costs in optimal BST.

- To help us keep track of the structure of optimal BST, define $root[i,j]$, for $1\le i\le j\le n$, to be the index $r$ for which $k_r$ is the root of an optimal BST containing keys $k_i,\ldots,k_j$.

## Step 3: Computing the expected search cost

A_i ... A_r ... A_j

![](img/09c68ab421cfce4995ddad1430ef2637_319_0.png)

![](img/09c68ab421cfce4995ddad1430ef2637_319_1.png)

```
e[i, j] = { q_{i-1} if j = i-1, min_{i ≤ r ≤ j} { e[i, r-1] + e[r+1, j] + w[i, j] } if i ≤ j. (15.19)
```

- Similarity: optimal BST and matrix-chain multiplication.

- A direct, recursive implementation would be as inefficient.

- Store the e[i,j] values in a table e[1.. n+1, 0.. n].

  - The first index runs to n+1, in order to have a subtree containing only d_n, need to compute and store e[n+1, n].

  - The second index starts from 0, in order to have a subtree containing only d_0, need to compute and store e[1, 0].

- Use a table root[i,j], for recording the root of the subtree containing keys k_i, ..., k_j, only for 1 ≤ i ≤ j ≤ n.

- Other table for efficiency.
- $e[i,j] = e[i,r-1] + e[r+1,j] + w[i,j]$  (15.18)
- Rather than compute the value of $w[i,j]$ every time we are computing $e[i,j]$—which would take $\Theta(j-i)$ additions—we store these values in a table $w[1..n+1, 0..n]$.
- （无需每次计算 $e[i,j]$ 时都计算 $w[i,j]$，...）
- For the base case, we compute $w[i,i-1] = q_{i-1}$ for $1\le i\le n$.
- For $j\ge i$, $w[i,j] = \sum_{l=i}^{j} p_l + \sum_{l=i-1}^{j} q_l = w[i,j-1] + p_j + q_j$  (15.20)
- Thus, compute the $\Theta(n^2)$ values of $w[i,j]$ in $\Theta(1)$ time each.
- Inputs: the probabilities $p_1, ..., p_n$ and $q_0, ..., q_n$ and the size $n$
