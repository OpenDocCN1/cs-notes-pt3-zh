

## 马尔可夫链（Markov Chain）

- 一个状态的边缘分布可以表示为
- 
- $p(z^{(m+1)}) = \sum_{z^{(m)}} p(z^{(m+1)}|z^{(m)})p(z^{(m)})$
- 平稳性（Stationary,或不变性 Invariant）
- 
- $p^*(z) = \sum_{z'} T(z',z)p^*(z')$
- 细致平稳（Detailed balance）-充分条件
- 
- $p^*(z)T(z,z') = p^*(z')T(z',z)$
- 
- $\sum_{z'} p^*(z')T(z',z) = \sum_{z'} p^*(z)T(z,z') = p^*(z)\sum_{z'} p(z'|z) = p^*(z)$

当 $m \to \infty$ 马尔可夫链各状态趋于平稳，即

$p_m = p_{m-1}T \xrightarrow{m \to \infty} p = pT$

$p = [p(1),...,p(j),...]$

平稳分布

同时

$\lim_{m \to \infty} T^m = \begin{bmatrix} p(1),...,p(j),... \\ p(1),...,p(j),... \\ ..., ... \\ p(1),...,p(j),... \\ ..., ... \end{bmatrix}$ $\sum_j p(j)=1$

## Metropolis-Hastings 方法

- 思想：对于需要采样的一分布 $p(z)$，构造一个转移矩阵为 $T$ 的马尔可夫链，使它的平稳分布恰好为 $p(z)$
- 假设有一个转移矩阵 $Q(z, z') = q(z'|z)$，$q(z)$为容易采样的分布
- 通常情况下，该转移矩阵难以满足细致平稳条件
- $p(z)q(z'|z) \neq p(z')q(z|z')$
- 引入 $a(z, z')$ 使
- $p(z)q(z'|z)a(z, z') = p(z')q(z|z')a(z', z)$

其中：
$a(z, z') = p(z')q(z|z')$
$a(z', z) = p(z)q(z'|z)$
} 接受率

在细致平稳条件两边乘以因子 $C$

$p(z)q(z'|z)a(z,z') \cdot C = p(z')q(z|z')a(z',z) \cdot C$

细致平稳条件并没有打破！！！

同比例放大 $a(z,z')$, $a(z',z)$ 使最大的为 1，令

$A(z,z') = \min\left\{1, \frac{p(z)q(z'|z)}{p(z')q(z|z')}\right\}$

$= \min\left\{1, \frac{\tilde{p}(z)q(z'|z)}{\tilde{p}(z')q(z|z')}\right\}$  $p(z) = \frac{1}{Z_p}\tilde{p}(z)$

## Metropolis-Hastings 方法

- ● **步骤：**
- 
- 1、**初始化**马尔可夫链状态 $z=z_0$
- 
- 2、对 $\tau=1,2,\ldots$ **循环以下过程采样**
- 
- 1) 第 $\tau$ 个时刻马尔可夫链状态为 $z=z^{(\tau)}$，采样 $z^*=q(z\mid z^{(\tau)})$
- 
- 2) 从均匀分布中采样 $u\sim\operatorname{uniform}[0,1]$
- 
- 3) 如果 $u<A(z^{(\tau)},z^*)=\min\left\{1,\frac{\tilde p(z^*)q(z'\mid z^*)}{\tilde p(z')q(z^*\mid z')}\right\}$，则接受 $z^{(\tau+1)}=z^*$
- 
- 4) 否则 $z^{(\tau+1)}=z^{(\tau)}$

## 吉布斯采样（Gibbs Sampling）

- - 一种特殊的M-H采样算法
- - 针对多元分布进行采样　$p(z)=p(z_1,\ldots,z_M)$

**每次只改变一个维度上的值，保持其他维度不变**

$p(z_1,z_2,z_3)$

首先：初始化 $(z_1^{(0)}, z_2^{(0)}, z_3^{(0)})$

在第 $\tau$ 步，假设已经产生了 $(z_1^{(\tau)}, z_2^{(\tau)}, z_3^{(\tau)})$

- ➡ 根据 $p(z_1\mid z_2^{(\tau)},z_3^{(\tau)})$ 产生 $z_1^{(\tau+1)}$
- ➡ 根据 $p(z_2\mid z_1^{(\tau+1)},z_3^{(\tau)})$ 产生 $z_2^{(\tau+1)}$
- ➡ 根据 $p(z_3\mid z_1^{(\tau+1)},z_2^{(\tau+1)})$ 产生 $z_3^{(\tau+1)}$

## 与M-H的关系

- 建议概率：
- $q_k(\mathbf{z}^*|\mathbf{z}) = p(z_k^*|\mathbf{z}_{\setminus k})$
- 接受概率：
- $A_k(z^*, z^{(\tau)}) = \min\left\{1, \frac{\tilde{p}(z^*) q_k(z^{(\tau)}|z^*)}{\tilde{p}(z^{(\tau)}) q_k(z^*|z^{(\tau)})}\right\}$

$p(\mathbf{z}) = p(z_k|\mathbf{z}_{\setminus k})p(\mathbf{z}_{\setminus k}) \quad \mathbf{z}^*_{\setminus k} = \mathbf{z}_{\setminus k}$

$A(\mathbf{z}^*, \mathbf{z}) = \frac{p(\mathbf{z}^*) q_k(\mathbf{z}|\mathbf{z}^*)}{p(\mathbf{z}) q_k(\mathbf{z}^*|\mathbf{z})} = \frac{p(z_k^*|\mathbf{z}^*_{\setminus k})p(\mathbf{z}^*_{\setminus k})p(z_k|\mathbf{z}^*_{\setminus k})}{p(z_k|\mathbf{z}_{\setminus k})p(\mathbf{z}_{\setminus k})p(z_k^*|\mathbf{z}_{\setminus k})} = 1$

## 概率图模型

概率图模型 (Probabilistic Graphical Model) 是一类用图来表达变量相关关系的概率模型

图模型提供了一种描述框架

- 节点：随机变量或集合
- 边：随机变量之间的关系

![](img/292e77b9b7b40db2ea6f49ac62f8aa0f_1115_0.png)

![](img/292e77b9b7b40db2ea6f49ac62f8aa0f_1115_1.png)

## 概率图模型

### ● 概率图模型分类

- ➢ 有向图：贝叶斯网
- ➢ 无向图：马尔可夫网

![](img/292e77b9b7b40db2ea6f49ac62f8aa0f_1116_0.png)

![](img/292e77b9b7b40db2ea6f49ac62f8aa0f_1116_1.png)

## 概率图模型

### 🔴 联合概率分布

![](img/292e77b9b7b40db2ea6f49ac62f8aa0f_1117_0.png)

$p(x_1,\ldots,x_7)=p(x_1)p(x_2)p(x_3)p(x_4\mid x_1,x_2,x_3)p(x_5\mid x_1,x_3)p(x_6\mid x_4)p(x_7\mid x_4,x_5)$

$p(\mathbf{x})=\prod_{k=1}^{K}p(x_k\mid\mathbf{pa}_k)$

## 马尔可夫随机场

- - 分布形式化：
- - 使用基于极大团的势函数（因子）
- - 对于图中节点的一个子集，若其中任意两节点间都有边连接，则称该节点子集为一个“团”（clique）。若一个团中加入另外任何一个节点都不再形成团，则称该团为“极大团”（maximal clique）
- - 图中{x₁, x₂}, {x₂, x₆}, {x₂, x₅, x₆}等为团
- - 图中{x₂, x₆}不是极大团
- - 每个节点至少出现在一个极大团中
- - 多个变量之间的连续分布可基于团分解为多个因子的乘积

![](img/292e77b9b7b40db2ea6f49ac62f8aa0f_1119_0.png)

