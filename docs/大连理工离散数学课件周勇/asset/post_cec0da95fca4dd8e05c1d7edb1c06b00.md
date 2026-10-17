
## 集合定律

- $S_{13}\quad A \cap (B \cup C) = (A \cap B) \cup (A \cap C)$ 分配律
- $S_{14}\quad A \cup (B \cap C) = (A \cup B) \cap (A \cup C)$
- $S_{15}\quad \sim\sim A = A$ 双重否定律
- $S_{16}\quad \sim(A \cap B) = \sim A \cup \sim B$ 德·摩根律
- $S_{17}\quad \sim(A \cup B) = \sim A \cap \sim B$
- $S_{18}\quad A \cap A = A$ 等幂律
- $S_{19}\quad A \cup A = A$
- $S_{20}\quad A \cap \sim A = \varnothing$ 补余律
- $S_{21}\quad A \cup \sim A = E$
- $S_{22}\quad A \cap E = A$ 同一律
- $S_{23}\quad A \cup \varnothing = A$
- $S_{24}\quad A - \varnothing = A$
- $S_{25}\quad A \oplus \varnothing = A$
- $S_{26}\quad A \cap \varnothing = \varnothing$ 零律
- $S_{27}\quad A \cup E = E$ 零律
- $S_{28}\quad A \cup (A \cap B) = A$ 吸收律
- $S_{29}\quad A \cap (A \cup B) = A$ 吸收律
- $S_{30}\quad \sim \varnothing = E$
- $S_{31}\quad \sim E = \varnothing$
- $S_{32}\quad A \oplus A = \varnothing$
- $S_{33}\quad A \cap (B - A) = \varnothing$
- $S_{34}\quad A \cup (B - A) = A \cup B$
- $S_{35}\quad A - (B \cup C) = (A - B) \cap (A - C)$
- $S_{36}\quad A - (B \cap C) = (A - B) \cup (A - C)$
- $S_{37}\quad A - B = A \cap \sim B$
- $S_{38}\quad A \oplus B = (A \cap \sim B) \cup (\sim A \cap B)$
- $S_{39}\quad (A \cup B \neq \varnothing) \Rightarrow (A \neq \varnothing) \vee (B \neq \varnothing)$
- $S_{40}\quad (A \cap B \neq \varnothing) \Rightarrow (A \neq \varnothing) \wedge (B \neq \varnothing)$

**证明：**（39）转化为假设 $(A \neq \varnothing) \vee (B \neq \varnothing)$ 为假，证明 $A \cup B \neq \varnothing$ 为假。

由 $(A \neq \varnothing) \vee (B \neq \varnothing)$ 为假可知，$A \neq \varnothing$ 和 $B \neq \varnothing$ 均为假，即 $A = \varnothing$ 且 $B = \varnothing$，也就是 $A \cup B = \varnothing$，使得 $A \cup B \neq \varnothing$ 为假。

## 3.3 包含排斥原理

集合的运算，可用于有限个元素的计数问题。
设 $A_1,A_2$ 是有限集合，用 $|A_1|,|A_2|$ 分别表示它们的基数，那么可以推出：

- $|A_1 \cup A_2| \le |A_1| + |A_2|$
- $|A_1 \cap A_2| \le \min(|A_1|, |A_2|)$
- $|A_1 - A_2| \ge |A_1| - |A_2|$
- $|A_1 \oplus A_2| = |A_1| + |A_2| - 2|A_1 \cap A_2|$

**定理3.4-1：** 设 $A_1,A_2$ 是有限集合，$|A_1|,|A_2|$ 为其基数，则

$$
|A_1 \cup A_2| = |A_1| + |A_2| - |A_1 \cap A_2|
$$

**证：**

(1) 当 $A_1$ 和 $A_2$ 不相交，即 $A_1 \cap A_2 = \varnothing$ 时，

$$
|A_1 \cup A_2| = |A_1| + |A_2| = |A_1| + |A_2| - |A_1 \cap A_2|
$$

(2) 当 $A_1 \cap A_2 \neq \varnothing$ 时，那么

$$
|A_1| = |A_1 \cap \sim A_2| + |A_1 \cap A_2|
$$

$$
|A_2| = |\sim A_1 \cap A_2| + |A_1 \cap A_2|
$$

所以

$$
|A_1| + |A_2| = |A_1 \cap \sim A_2| + |\sim A_1 \cap A_2| + 2|A_1 \cap A_2|
$$

由于

$$
|A_1 \cap \sim A_2| + |\sim A_1 \cap A_2| + |A_1 \cap A_2| = |A_1 \cup A_2|
$$

因此

$$
|A_1 \cup A_2| = |A_1| + |A_2| - |A_1 \cap A_2|
$$

**例：** 假设在10名青年中有5名是工人，7名是学生，其中兼具有工人与学生双重身份的青年有三名，问既不是工人又不是学生的青年有几名？

**解：** 设工人的集合为 $W$，学生的集合为 $S$，则根据题设应有：

$$
|W| = 5,\quad |S| = 7,\quad |W \cap S| = 3
$$

又因为 $|\sim W \cap \sim S| + |W \cup S| = 10$，则

$$
|\sim W \cap \sim S| = 10 - |W \cup S|
= 10 - (|W| + |S| - |W \cap S|)
= 10 - (5 + 7 - 3) = 1
$$

因此既不是工人又不是学生的青年有1人。

包含排斥原理在三个有限集合上的推广：

$$
|A_1 \cup A_2 \cup A_3| = |A_1| + |A_2| + |A_3| - \left( |A_1 \cap A_2| + |A_1 \cap A_3| + |A_2 \cap A_3| \right) + |A_1 \cap A_2 \cap A_3|
$$

![](img/d475a943ed426379b80e793b9fe1f17d_297_0.png)

**例：** 某工厂装配30辆汽车，可供选择的设备是收音机、空气调节器和对讲机。已知其中15辆汽车有收音机、8辆有空气调节器，6辆有对讲机，而且其中有3辆这三种设备都有。我们希望知道有几辆汽车没有提供任何设备。

**解：** 设 $A_1$、$A_2$ 和 $A_3$ 分别表示配有收音机、空气调节器和对讲机的汽车集合，因此由题设知

$$
|A_1| = 15,\quad |A_2| = 8,\quad |A_3| = 6,\quad |A_1 \cap A_2 \cap A_3| = 3
$$

因为

$$
|A_1 \cap A_2| \ge |A_1 \cap A_2 \cap A_3| = 3
$$

$$
|A_1 \cap A_3| \ge |A_1 \cap A_2 \cap A_3| = 3
$$

$$
|A_2 \cap A_3| \ge |A_1 \cap A_2 \cap A_3| = 3
$$

得

$$
\begin{aligned}
|A_1 \cup A_2 \cup A_3|
&= 15 + 8 + 6 - |A_1 \cap A_2| - |A_1 \cap A_3| - |A_2 \cap A_3| + 3 \\
&\le 32 - 3 - 3 - 3 = 23
\end{aligned}
$$

把包含排斥原理推广到 $n$ 个集合。

**定理3.4-2：** 设 $A_1,A_2,\ldots,A_n$ 为 $n$ 个有限集合，它们的基数分别为 $|A_1|,|A_2|,\ldots,|A_n|$，可得：

$$
\begin{aligned}
|A_1 \cup A_2 \cup \cdots \cup A_n|
&= \sum_{i=1}^n |A_i| - \sum_{1 \le i < j \le n} |A_i \cap A_j| \\
&\quad + \sum_{1 \le i < j < k \le n} |A_i \cap A_j \cap A_k| + \cdots + (-1)^{n-1} |A_1 \cap A_2 \cap \cdots \cap A_n|
\end{aligned}
$$
