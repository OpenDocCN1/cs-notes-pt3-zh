

## 16.3.1 前缀码

| a | b | c | d | e | f |
|---|---|---|---|---|---|
| 0 | 101 | 100 | 111 | 1101 | 1100 |

001011101 唯一地表示为 0·0·101·1101，解码为“aabe”。

![](img/09c68ab421cfce4995ddad1430ef2637_467_0.png)

### • 解码

- ◆ 我们将字符的二进制码字解释为从根到该字符的路径。
- （将字符的二叉码表示解释为一条路径：从树根到树叶）
- ◆ 不是二叉搜索树，因为叶子不必按排序顺序出现，并且内部节点不包含字符键。
- （不是二叉搜索树）

![](img/09c68ab421cfce4995ddad1430ef2637_467_1.png)

## 16.3.1 前缀码

![](img/09c68ab421cfce4995ddad1430ef2637_468_0.png)

- - 文件的最优码始终由一个 *full* 二叉树（满二叉树）表示，每个非叶节点都有两个子节点（Ex16.3-1）。我们示例中的定长码不是最优的。
- - 我们可以将注意力限制在满二叉树上
  - C 是字母表，
  - 所有字符频率 >0
  - 最优前缀码的树有 |C| 个叶子，每个字母一个，恰好有 |C|-1 个内部节点。

## 16.3.1 前缀码

![](img/09c68ab421cfce4995ddad1430ef2637_469_0.png)

### 计算编码文件所需的位数

- - 给定对应于前缀码的树 $T$，对于字母表 $C$ 中的每个字符 $c$，
  - $f(c)$：文件中 $c$ 的频率
  - $d_T(c)$：树中 $c$ 的叶子的深度（字符 $c$ 的码字的长度）。那么，编码文件所需的位数

$$B(T)=\sum_{c\in C} f(c)d_T(c) \qquad (16.5)$$

我们将其定义为树 $T$ 的 *cost*。

## 16.3.2 构造 Huffman 码

**Huffman code:**  
一种贪心算法  
构造  
最优前缀码

```
HUFFMAN(C)
1  n ← |C|
2  Q ← C
3  for i ← 1 to n − 1
4      allocate(分配) a new node z
5      left[z] ← x ← EXTRACT-MIN(Q)
6      right[z] ← y ← EXTRACT-MIN(Q)
7      f[z] ← f[x] + f[y]
8      INSERT(Q, z)
9  return EXTRACT-MIN(Q)  //return the root of the tree.
```

- - **C**：*n* 个字符的集合，*c* ∈ **C**：具有频率 *f*[*c*] 的对象。
  - 构建对应于最优码的树 *T*。
  - 从 |*C*| 个叶子开始，进行 |*C*|−1 次“合并”操作。
  - 一个以 *f* 为关键的最小优先队列 *Q*，用于识别要合并的两个频率最低的对象。合并的结果是一个新对象，其频率是被合并的两个对象的频率之和。

## 16.3.2 构造 Huffman 码

示例：
Huffman 算法进行。6 个字母，
5 次合并步骤。
最终树表示最优前缀码。

```
HUFFMAN(C)
1 n ← |C|
2 Q ← C
3 for i ← 1 to n - 1
4   allocate(分配) a new node z
5   left[z] ← x ← EXTRACT-MIN (Q)
6   right[z] ← y ← EXTRACT-MIN (Q)
7   f[z] ← f[x] + f[y]
8   INSERT(Q, z)
9 return EXTRACT-MIN(Q) //return the root of the tree.
```

![](img/09c68ab421cfce4995ddad1430ef2637_471_0.png)

![](img/09c68ab421cfce4995ddad1430ef2637_471_1.png)

![](img/09c68ab421cfce4995ddad1430ef2637_471_2.png)

![](img/09c68ab421cfce4995ddad1430ef2637_471_3.png)

![](img/09c68ab421cfce4995ddad1430ef2637_471_4.png)

![](img/09c68ab421cfce4995ddad1430ef2637_471_5.png)

## 16.3.3 Huffman 算法的正确性

- - 确定最优前缀码的问题表现出 **greedy-choice** 和 **optimal-substructure** 属性。
- - **Lemma 16.2 (greedy-choice property)**
- 设 $C$ 为字母表，每个字符 $c \in C$ 具有频率 $f[c]$。
- $x$ 和 $y \in C$，并且具有最低的频率。则存在 $C$ 的一个最优前缀码，其中 $x$ 和 $y$ 的 **codewords** 具有相同的长度并且仅在最后一位上不同。
- *Proof idea:* 取表示任意最优前缀码的树 $T$，并对其进行修改以生成表示另一个最优前缀码的树，使得 $x$ 和 $y$ 出现在新树中最大深度的姊妹叶（姊妹叶）。

![](img/09c68ab421cfce4995ddad1430ef2637_472_0.png)

