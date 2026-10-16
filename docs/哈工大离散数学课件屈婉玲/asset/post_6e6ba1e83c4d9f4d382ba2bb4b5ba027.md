
## 集合论

### 集合论部分

- 第3章 集合的基本概念和运算
- 第4章 二元关系和函数

## 第3章 集合的基本概念和运算

- 3.1 集合的基本概念
- 3.2 集合的基本运算
- 3.3 集合中元素的计数

### 3.1 集合的基本概念

- 集合的定义与表示
- 集合与元素
- 集合之间的关系
- 空集
- 全集
- 幂集

### 集合定义与表示

集合没有精确的数学定义。

理解：一些离散个体组成的全体。

组成集合的个体称为它的元素或成员。

集合的表示：

列元素法：A = { a, b, c, d }

谓词表示法：B = { x | P(x) }

B 由使得 P(x) 为真的 x 构成。

常用数集：

N, Z, Q, R, C 分别表示自然数、整数、有理数、实数和复数集合，注意 0 是自然数。

### 集合与元素

元素与集合的关系：隶属关系。

属于 ∈，不属于 ∉。

实例：

A = { x | x∈R ∧ x²−1=0 }, A = {−1, 1}

1∈A, 2∉A

注意：对于任何集合 A 和元素 x（可以是集合），x∈A 和 x∉A 两者成立其一，且仅成立其一。

### 隶属关系的层次结构

例 3.1

A = { a, {b,c}, d, {{d}} }

{b,c}∈A

b∉A

{{d}}∈A

{d}∉A

d∈A

![](img/3e54617849435b84ab04e6656729f806_147_0.png)

### 集合之间的关系

包含（子集）：A ⊆ B ⇔ ∀x (x∈A → x∈B)

不包含：A ⊈ B ⇔ ∃x (x∈A ∧ x∉B)

相等：A = B ⇔ A ⊆ B ∧ B ⊆ A

不相等：A ≠ B

真包含：A ⊂ B ⇔ A ⊆ B ∧ A ≠ B

不真包含：A ⊄ B

思考：≠ 和 ⊄ 的定义。

注意：∈ 和 ⊆ 是不同层次的问题。

### 空集与全集

空集 ∅：不含任何元素的集合。

实例：{x | x²+1=0 ∧ x∈R} 就是空集。

定理：空集是任何集合的子集。

∅ ⊆ A ⇔ ∀x (x∈∅ → x∈A) ⇔ T

推论：空集是惟一的。

证：假设存在 ∅₁ 和 ∅₂，则 ∅₁⊆∅₂ 且 ∅₂⊆∅₁，因此 ∅₁=∅₂。

全集 E。

相对性：在给定问题中，全集包含任何集合，即 ∀A (A⊆E)。

### 3.2 集合的基本运算

- 集合基本运算的定义
  - ∪ ∩ − ∼ ⊕
- 文氏图（John Venn）
- 例题
- 集合运算的算律
- 集合包含或恒等式的证明

### 集合基本运算的定义

并：$A \cup B = \{ x \mid x \in A \lor x \in B \}$

交：$A \cap B = \{ x \mid x \in A \land x \in B \}$

相对补：$A - B = \{ x \mid x \in A \land x \notin B \}$

对称差：$A \oplus B = (A - B) \cup (B - A)$  
$= (A \cup B) - (A \cap B)$

绝对补：$\sim A = E - A$

### 文氏图表示

![](img/3e54617849435b84ab04e6656729f806_153_0.png)

![](img/3e54617849435b84ab04e6656729f806_153_1.png)

![](img/3e54617849435b84ab04e6656729f806_153_2.png)

![](img/3e54617849435b84ab04e6656729f806_153_3.png)

![](img/3e54617849435b84ab04e6656729f806_153_4.png)

### 关于运算的说明

- 运算顺序：∼ 和幂集优先，其他由括号确定。
- 并和交运算可以推广到有穷个集合上，即
  - $A_1 \cup A_2 \cup ... \cup A_n = \{x \mid x \in A_1 \lor x \in A_2 \lor ... \lor x \in A_n\}$
  - $A_1 \cap A_2 \cap ... \cap A_n = \{x \mid x \in A_1 \land x \in A_2 \land ... \land x \in A_n\}$
- 某些重要结果
  - $\varnothing \subseteq A - B \subseteq A$
  - $A \subseteq B \Leftrightarrow A - B = \varnothing$（后面证明）
  - $A \cap B = \varnothing \Leftrightarrow A - B = A$

### 例1

F：一年级大学生的集合　　S：二年级大学生的集合  
R：计算机系学生的集合　　M：数学系学生的集合  
T：选修离散数学的学生集合  
L：爱好文学学生的集合　　P：爱好体育运动学生的集合

所有计算机系二年级学生都选修离散数学。

数学系一年级的学生都没有选修离散数学。

数学系学生或爱好文学或爱好体育运动。

只有一、二年级的学生才爱好体育运动。

除去数学和计算机系二年级学生外都不选修离散数学。

T ⊆ (M ∪ R) ∩ S

R ∩ S ⊆ T

(M ∩ F) ∩ T = ∅

M ⊆ L ∪ P

P ⊆ F ∪ S

S − (M ∪ R) ⊆ P

### 集合运算的算律

| | ∪ | ∩ | ⊕ |
|---|---|---|---|
| 交换 | A∪B=B∪A | A∩B=B∩A | A⊕B=B⊕A |
| 结合 | (A∪B)∪C = A∪(B∪C) | (A∩B)∩C = A∩(B∩C) | (A⊕B)⊕C = A⊕(B⊕C) |
| 幂等 | A∪A=A | A∩A=A |  |

| | ∪与∩ | ∩与⊕ |
|---|---|---|
| 分配 | A∪(B∩C)=(A∪B)∩(A∪C)；A∩(B∪C)=(A∩B)∪(A∩C) | A∩(B⊕C)=(A∩B)⊕(A∩C) |
| 吸收 | A∪(A∩B)=A；A∩(A∪B)=A |  |

吸收律的前提：∪、∩ 可交换。

### 集合运算的算律（续）

| | - | ∼ |
|---|---|---|
| *D.M 律* | $A-(B\cup C)=(A-B)\cap(A-C)$<br>$A-(B\cap C)=(A-B)\cup(A-C)$ | $\sim(B\cup C)=\sim B\cap\sim C$<br>$\sim(B\cap C)=\sim B\cup\sim C$ |
| 双重否定 |  | $\sim\sim A=A$ |

| | ∅ | E |
|---|---|---|
| 补元律 | $A\cap\sim A=\varnothing$ | $A\cup\sim A=E$ |
| 零律 | $A\cap\varnothing=\varnothing$ | $A\cup E=E$ |
| 同一律 | $A\cup\varnothing=A$ | $A\cap E=A$ |
| 否定 | $\sim\varnothing=E$ | $\sim E=\varnothing$ |

### 集合包含或相等的证明方法

- 证明 $X \subseteq Y$
  - 命题演算法
  - 包含传递法
  - 等价条件法
  - 反证法
  - 并交运算法
- 证明 $X = Y$
  - 命题演算法
  - 等式代入法
  - 反证法
  - 运算法

以上的 $X, Y$ 代表集合公式。

### 命题演算法证 X⊆Y

任取 x，

x∈X ⇒ ... ⇒ x∈Y

例3 证明 A⊆B ⇔ P(A)⊆P(B)

任取 x

x∈P(A) ⇒ x⊆A ⇒ x⊆B ⇒ x∈P(B)

任取 x

x∈A ⇒ {x}⊆A ⇒ {x}∈P(A) ⇒ {x}∈P(B)

⇒ {x}⊆B ⇒ x∈B

### 包含传递法证 X⊆Y

找到集合 $T$ 满足 $X \subseteq T$ 且 $T \subseteq Y$，从而有 $X \subseteq Y$。

例4 $A - B \subseteq A \cup B$

证：$A - B \subseteq A$，$A \subseteq A \cup B$，所以 $A - B \subseteq A \cup B$。
