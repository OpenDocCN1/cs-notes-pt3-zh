
- $r_{ii}=0$，$w_{ii}=q_i$，$0 \le i \le n$。
- $a_1, \ldots, a_n$ 的最优二叉搜索树为 $T_{0n}$。其代价为 $c_{0n}$，根为 $r_{0n}$。

如果 $T_{ij}$ 是 $a_{i+1}, \ldots, a_j$ 的最优二叉搜索树，且 $r_{ij}=k$，$i < k \le j$，那么 $T_{ij}$ 有 2 棵子树 L 和 R。

- L 包含标识符 $a_{i+1}, \ldots, a_{k-1}$。
- R 包含标识符 $a_{k+1}, \ldots, a_j$。

![](img/15e8d7d94d8ddf02cb6839870195a31e_753_0.png)

$T_{ij}$ 的代价 $c_{ij}$ 为

$$c_{ij} = p_k + \operatorname{cost}(L) + \operatorname{cost}(R) + w_{i,k-1} + w_{kj} \quad (10.2)$$

由 (10.2) 可知，若要使 $c_{ij}$ 最小，则须有 $\operatorname{cost}(L)=c_{i,k-1}$ 且 $\operatorname{cost}(R)=c_{kj}$，否则我们可以用代价更小的子树替换 L 或 R，从而为 $a_{i+1}, \ldots, a_j$ 生成一棵代价低于 $c_{ij}$ 的二叉搜索树。这就违反了 $T_{ij}$ 是最优的假设。

因此，式 (10.2) 变为

$$c_{ij} = p_k + w_{i,k-1} + w_{kj} + c_{i,k-1} + c_{kj} = w_{ij} + c_{i,k-1} + c_{kj} \quad (10.3)$$

由于 $T_{ij}$ 是最优的，由 (10.3) 可知 $r_{ij}=k$ 满足

$$w_{ij}+c_{i,k-1}+c_{kj}=\min_{i<l\le j}\{w_{ij}+c_{i,l-1}+c_{lj}\}$$

或

$$c_{i,k-1}+c_{kj}=\min_{i<l\le j}\{c_{i,l-1}+c_{lj}\} \quad (10.4)$$

### 另请注意

$$w_{ij}=w_{i,j-1}+p_j+q_j.$$

(10.4) 为我们提供了一种从 $r_{ii}=0$、$T_{ii}=\varnothing$ 和 $c_{ii}=0$ 出发，求得 $r_{0n}$、$T_{0n}$ 和 $c_{0n}$ 的方法。

## 示例 10.2

设 $n=4$，$(a_1, a_2, a_3, a_4)=(do, if, return, while)$。

设 $(p_1, p_2, p_3, p_4)=(3,3,1,1)$，$(q_0, q_1, q_2, q_3, q_4)=(2,3,1,1,1)$。

为方便起见，p 和 q 均取整数。

初始时，$w_{ii}=q_i$，$r_{ii}=0$，$c_{ii}=0$，$0 \le i \le 4$。

利用 (10.3) 和 (10.4)，我们得到

$$w_{01}=p_1+w_{00}+w_{11}=p_1+q_1+w_{00}=8$$

$$c_{01}=w_{01}+\min\{c_{00}+c_{11}\}=8$$

$$r_{01}=1$$

$$w_{12}=p_2+w_{11}+w_{22}=p_2+q_2+w_{11}=7$$

$$c_{12}=w_{12}+\min\{c_{11}+c_{22}\}=7$$

$$r_{12}=2$$

$$w_{23}=p_3+w_{22}+w_{33}=p_3+q_3+w_{22}=3$$

$$c_{23}=w_{23}+\min\{c_{22}+c_{33}\}=3$$

$$r_{23}=3$$

$$w_{34}=p_4+w_{33}+w_{44}=p_4+q_4+w_{33}=3$$

$$c_{34}=w_{34}+\min\{c_{33}+c_{44}\}=3$$

$$r_{34}=4$$

| i \ j-i | 0 | 1 | 2 | 3 | 4 |
|---|---|---|---|---|---|
| 0 | w₀₀=2<br>c₀₀=0<br>r₀₀=0 | w₁₁=3<br>c₁₁=0<br>r₁₁=0 | w₂₂=1<br>c₂₂=0<br>r₂₂=0 | w₃₃=1<br>c₃₃=0<br>r₃₃=0 | w₄₄=1<br>c₄₄=0<br>r₄₄=0 |
| 1 | w₀₁=8<br>c₀₁=8<br>r₀₁=1 | w₁₂=7<br>c₁₂=7<br>r₁₂=2 | w₂₃=3<br>c₂₃=3<br>r₂₃=3 | w₃₄=3<br>c₃₄=3<br>r₃₄=4 | |
| 2 | w₀₂=12<br>c₀₂=19<br>r₀₂=1 | w₁₃=9<br>c₁₃=12<br>r₁₃=2 | w₂₄=5<br>c₂₄=8<br>r₂₄=3 | | |
| 3 | w₀₃=14<br>c₀₃=25<br>r₀₃=2 | w₁₄=11<br>c₁₄=19<br>r₁₄=2 | | | |
| 4 | w₀₄=16<br>c₀₄=32<br>r₀₄=2 | | | | |

根据表中的数据，可以按下图构造出 $T_{04}$：

![](img/15e8d7d94d8ddf02cb6839870195a31e_760_0.png)

示例 10.2 的最优二叉搜索树

一般地，我们需要对所有 $j-i=1,2,\ldots,n$ 计算 $c_{ij}$。

对于每个 $j-i=m$，需要计算 $n-m+1$ 个 $c_{ij}$（即 $c_{0m},\ldots,c_{n-m,n}$）。

每个 $c_{ij}$ 的计算都需要从 (10.4) 的 $m$ 个量中求出最小值——需要 $O(m)$ 时间。

所有满足 $j-i=m$ 的 $c_{ij}$ 的总时间为 $O((n-m)m)$。

总时间为

$$\sum_{1\le m\le n} (n-m)m = O(n^3)$$

事实上，Knuth 证明了 (10.4) 中的最优 $l$ 可以通过将搜索范围限制在 $r_{i,j-1} \le l \le r_{i+1,j}$ 来找到。此时计算时间变为 $O(n^2)$。算法 obst 就使用了这一结果。

第 5 章的 BST 类被扩展，增加了私有成员函数 obst，并拥有了私有数据成员 $r$、$c$ 和 $w$。

下面是算法 obst。

```cpp
template <class KeyType>
void BST<KeyType>::obst(int *p, int *q, Element<KeyType> *a, int n)
// given a1 < a2 < ... < an, and pj, 1 <= j <= n, and qi, 0 <= i <= n, compute cij
// for Tij for a_{i+1}, ..., aj. Also compute rij and wij.
{
    for (int i = 0; i < n; i++) {
        w[i][i] = q[i]; r[i][i] = c[i][i] = 0;    // initialize
        w[i][i+1] = q[i] + q[i+1] + p[i+1]; // optimal trees with one node
        r[i][i+1] = i + 1;
        c[i][i+1] = w[i][i+1];
    }
    w[n][n] = q[n]; r[n][n] = c[n][n] = 0;

    for (int m = 2; m <= n; m++) // find optimal b.s.t. with m nodes
        for (int i = 0; i <= n - m; i++) {
            int j = i + m;
            w[i][j] = w[i][j-1] + p[j] + q[j];
            int k = KnuthMin(i, j);
            // KnuthMin returns k in the range [r[i][j-1], r[i+1][j]]
            // minimizing c[i][k-1] + c[k][j]
            c[i][j] = w[i][j] + c[i][k-1] + c[k][j]; // Eq. (10.3)
            r[i][j] = k;
        }
} // end of obst
```

实际的 $T_{0n}$ 可以由 $r_{ij}$ 在 $O(n)$ 时间内构造出来。

习题：P562-3

