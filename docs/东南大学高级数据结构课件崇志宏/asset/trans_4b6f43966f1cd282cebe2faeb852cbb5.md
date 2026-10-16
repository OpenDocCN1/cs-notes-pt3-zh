

## 按顺序插入伸展树

![](img/e8cfdb0a049dc5ab9d802234ebc2190e_78_0.png)

在BST中，用N个有序元素构建树的时间复杂度为O(N²)。那么用N个有序元素构建伸展树的性能如何？

## 伸展操作的一个极端示例

![](img/e8cfdb0a049dc5ab9d802234ebc2190e_79_0.png)

![](img/e8cfdb0a049dc5ab9d802234ebc2190e_79_1.png)

在节点“X”处进行伸展操作后

原始树

## 伸展树代码

- 伸展操作从节点开始“沿树向上”执行，直到根节点。
- 如何沿树“向上”遍历？
- 如何判断X和P是否同为左/右孩子，还是属于不同类型的孩子？
- 如何判断X是否存在祖父节点？
- 这种技术有什么缺点？

- 恒定的权重 \(w(v)>0\)（用于分析时，可为任意值）
- \(weight\ sum\ s(x)=\sum_{y\in subtree(x)}w(y)\)（其中subtree(x)是以\(x\)为根的子树，包含\(x\)）
- \(rank\ r(x)=\log s(x)\)

我们用\(r(x)\)作为节点的势。经过\(i\)次操作后的势函数为\(\Phi_i=\sum_{x\in tree(T)}r(x)\)。

## 引理1 对节点x执行一次伸展步骤的摊还代价≤ 3(r′(x) − r(x)) + 1，其中r为伸展步骤前的秩，r′为伸展步骤后的秩。此外，rr、ll、lr和rl伸展步骤的摊还代价≤ 3(r′(x) − r(x))。

![](img/e8cfdb0a049dc5ab9d802234ebc2190e_82_0.png)

我们仅考虑rr伸展步骤（参见图3.1）。该伸展步骤的实际代价为2（对应2次旋转）。伸展步骤只影响节点x、y、z的势/秩；我们观察到r′(x) = r(z)，r(y) ≥ r(x)，且r′(y) ≤ r′(x)。

\[
\begin{aligned}
\text{摊还代价} &= 2+\phi(i+1)-\phi(i)\\
&=2+\bigl(r'(x)+r'(y)+r'(z)\bigr)-\bigl(r(x)+r(y)-r(z)\bigr)\\
&=2+\bigl(r'(x)-r(z)\bigr)+r'(y)+r'(z)-r(x)-r(y)\\
&\le 2+0+r'(x)+r'(z)-r(x)-r(x)\\
&=2+r'(x)+r'(z)-2r'(x)
\end{aligned}
\]

对数函数是凹函数，即\(\frac{\log a+\log b}{2}\le \log\left(\frac{a+b}{2}\right)\)。因此我们还有（\(s\)为伸展步骤前的权重和，\(s'\)为伸展步骤后的权重和）：

\[
\frac{\log(s(x))+\log(s'(z))}{2}\le \log\left(\frac{s(x)+s'(z)}{2}\right)
\]

\[
\frac{r(x)+r'(z)}{2}\le \log\left(\frac{s(x)+s'(z)}{2}\right)\qquad\text{（注意 }s(x)+s'(z)\le s'(x)\text{）}
\]

\[
\begin{aligned}
&\le \log\left(\frac{s'(x)}{2}\right)\\
&=r'(x)-1\\
r'(z)&\le 2r'(x)-r(x)-2
\end{aligned}
\]

## **推论1**  *对节点x执行一次伸展操作的摊还代价为O(log n)。*

## **证明：**

对*x*执行一次伸展操作的摊还代价等于对*x*执行的所有相关伸展步骤的摊还代价之和：

```
$$\begin{aligned}
\text{摊还代价} &= \sum_i \text{代价}(\text{伸展步骤}_i) \\
&\leq \sum_i \left(3(r^{i+1}(x)-r^i(x))+1\right) \\
&= 3(r(\text{根})-r(x))+1
\end{aligned}$$
```

+1来自最后的*r*或*r*伸展步骤（如有必要）。如果对树中所有节点设置*w(v) = 1*，则*r(root) = log n*，于是有：

```
$$\text{摊还代价} \leq 3\log n + 1 = O(\log n)$$
```

## 路漫漫其修远兮！

## 为什么学习高级数据结构？
- 内容
- 第1周：数据结构与计算机科学、算法、数据库、万维网……
- 数据结构原理——如何实现？
- 第2周：为什么以及如何实现O(log n)访问时间？
- 第3周：动态数据结构与分析
- 第4周：随机化数据结构
- 第5周：增强数据结构
- 第6周：分布式环境中的数据结构
- 新问题——应用
- 第7周：研究前沿中的数据结构
- 第8周：考试

## 哈夫曼编码

- FP-Tree
- 草图（Sketches）

![](img/e8cfdb0a049dc5ab9d802234ebc2190e_90_0.png)

![](img/e8cfdb0a049dc5ab9d802234ebc2190e_90_1.png)

![](img/e8cfdb0a049dc5ab9d802234ebc2190e_90_2.png)

![](img/e8cfdb0a049dc5ab9d802234ebc2190e_90_3.png)

![](img/e8cfdb0a049dc5ab9d802234ebc2190e_90_4.png)

a.

b.

c.

d.

e.

