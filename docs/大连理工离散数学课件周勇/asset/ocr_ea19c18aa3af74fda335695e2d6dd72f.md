# # 实例

例2 判断下列偏序集是否构成格，并说明理由。
(1) \( <P(B), \subseteq> \)，其中 \( P(B) \) 是集合 \( B \) 的幂集。
(2) \( <\mathbb{Z}, \leq> \)，其中 \( \mathbb{Z} \) 是整数集，\( \leq \) 为小于或等于关系。
(3) 偏序集的哈斯图分别在下图给出。

![](bbox=[0.071, 0.398, 0.875, 0.734])

(1) 幂集格. \( \forall x, y \in P(B), \quad x \lor y \) 就是 \( x \cup y \)，\( x \land y \) 就是 \( x \cap y \).
(2) 是格. \( \forall x, y \in \mathbb{Z}, \quad x \lor y = \max(x, y), \quad x \land y = \min(x, y) \).
(3) 都不是格. 可以找到两个结点缺少最大下界或最小上界。