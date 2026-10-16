

## WeightedUnion 和 SimpleFind 的分析：

WeightedUnion 的时间是 O(1)

执行 find 的最大时间由以下决定：

> 引理 5.5：假设我们从单节点树的森林开始。设 T 是一个由加权合并序列创建的具有 m 个节点的树。T 的高度不超过 ⌊log₂ m⌋ + 1。

## 归纳证明：

m = 1，成立。

假设它对所有具有 i ≤ m-1 个节点的树都成立。

对于 i = m，设 T 是一个由 WeightedUnion 创建的具有 m 个节点的树。

考虑最后一次执行的合并，Union(k, j)。

设 j 树的节点数为 a，k 树的节点数为 m-a。 不失一般性，假设 1 ≤ a ≤ m/2。 那么 T 的高度要么与 k 相同，要么是 j 的 1 + 高度。

![](img/15e8d7d94d8ddf02cb6839870195a31e_411_0.png)

如果是前一种情况，T 的高度 ≤ ⌈log₂(m-a)⌉+1 ≤ ⌈log₂ m⌉+1。

如果是后一种情况，T 的高度 ≤ ⌈log₂ a⌉+2 ≤ ⌈log₂ m/2⌉+2 ≤ ⌈log₂ m⌉+1。

![](img/15e8d7d94d8ddf02cb6839870195a31e_413_0.png)

root(i)

i₁

i₂

i

root(i)

i₁

i₂

i

j = i, ..., i₂, i₁

```
```cpp
int Sets::CollapsingFind (int i )
{ // Find the root of tree containing element i. Use the
  // collapsing rule to collapse all nodes from i to the root.
  for (int r = i; parent[r] >= 0; r = parent[r]); // find the root
  while ( i != r) {
      int s = parent[i];
      parent[i] = r;
      i = s;
  }
  return r;
}
```
```

使用 WeightedUnion 和 CollapsingFind 处理合并和查找序列的最坏情况复杂度在引理5.6中陈述。

## 首先，一个增长非常缓慢的函数

$\alpha(p,q)=\min\{z\ge 1\mid A(z,\lfloor p/q\rfloor)>\log_2 q\},\ p\ge q\ge 1$

而阿克曼函数 $A(i,j)$ 定义为：

+   $A(1,j)=2^j$          for $j\ge1$  
+   $A(i,1)=A(i-1,2)$          for $i\ge2$  
+   $A(i,j)=A(i-1,A(i,j-1))$          for $i,j\ge2$

A(1, 2) = 2²

A(3,1) = A(2, 2) = A(1, A(2, 1)) = A(1, A(1, 2))
    = 2²² = 16

A(4,1) = A(3, 2) = A(2, A(3, 1)) = A(2, 16)
    = A(1, A(2, 15)) = 2^{A(2, 15)}
    = 2^{2^{A(2, 14)}} = ... = 2^{2^{...^{2}}} 16   (very big !)

因此对于任何实际的 p 和 q，α(p,q) ≤ 4。

## 引理 5.6 [Tarjan and Van Leeuwen]：假设我们从每棵树只有一个节点的森林开始。设 T(f, u) 为处理任意交错的 f 次查找和 u 次合并序列所需的最大时间。假设 u ≥ n/2，则

$$k_1(n+f\,\alpha(f+n,n)) \le T(f,u) \le k_2(n+f\,\alpha(f+n,n))$$

对于某些正常数 $k_1$ 和 $k_2$。

注意 T(f, u) 即使 $\alpha(f+n,n)$ 增长非常缓慢也不是线性的。

空间需求是每个元素一个节点。

## 5.10.3 应用于等价类

等价类 ⇔ 不相交集合

初始时，parent[i] = -1, 0 ≤ i ≤ n-1。

处理 i ≡ j，

令 x = find(i), y = find(j) --- 2 次查找

如果 x ≠ y 则 union(x, y) --- 最多 1 次合并

因此如果我们有 n 个元素和 m 个等价对，我们需要 2m 次查找和 min {n-1, m} 次合并。总时间为 O(n+2m α(n+2m,n))。

## 示例：

n = 12，处理等价对：
0 ≡ 4, 3 ≡ 1, 6 ≡ 10, 8 ≡ 9, 7 ≡ 4, 6 ≡ 8, 3 ≡ 5, 2 ≡ 11,
11 ≡ 0

![](img/15e8d7d94d8ddf02cb6839870195a31e_420_0.png)

(a) 初始树

(b) 处理 0 ≡ 4, 3 ≡ 1, 6 ≡10, 和 8 ≡ 9 之后

(c) 处理 7 ≡ 4, 6 ≡ 8, 3 ≡ 5, 和 2 ≡ 11 之后

[-5]

[-3]

[-4]

(d) 处理 11 ≡ 0 之后

# 练习：P316-3

## 5.12 计数二叉树

如果 n=0 或 1，只有 一棵二叉树。
如果 n=2，有两棵：

![](img/15e8d7d94d8ddf02cb6839870195a31e_424_0.png)

和

![](img/15e8d7d94d8ddf02cb6839870195a31e_424_1.png)

## 如果 n=3，有五棵：

![](img/15e8d7d94d8ddf02cb6839870195a31e_425_0.png)

有多少棵具有 n 个节点的不同的二叉树？在推导出解之前，让我们先研究另一个等价问题。

