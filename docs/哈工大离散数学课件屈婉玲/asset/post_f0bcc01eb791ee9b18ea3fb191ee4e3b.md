
## 反证法证 $X \subseteq Y$

欲证 $X \subseteq Y$, 假设命题不成立, 必存在 $x$ 使得 $x \in X$ 且 $x \notin Y$. 然后推出矛盾.

例6 证明 $A \subseteq C \land B \subseteq C \Rightarrow A \cup B \subseteq C$

证 假设 $A \cup B \subseteq C$ 不成立,

则 $\exists x\ (x \in A \cup B \land x \notin C)$

因此 $x \in A$ 或 $x \in B$, 且 $x \notin C$

若 $x \in A$, 则与 $A \subseteq C$ 矛盾;

若 $x \in B$, 则与 $B \subseteq C$ 矛盾.

## 利用已知包含式并交运算

由已知包含式通过运算产生新的包含式
X⊆Y ⇒ X∩Z⊆Y∩Z, X∪Z⊆Y∪Z

例7 证明 A∩C⊆B∩C ∧ A−C⊆B−C ⇒ A⊆B

证 A∩C⊆B∩C， A−C⊆B−C

上式两边求并，得

(A∩C)∪(A−C) ⊆ (B∩C)∪(B−C)

⇒ (A∩C)∪(A∩~C) ⊆ (B∩C)∪(B∩~C)

⇒ A∩(C∪~C) ⊆ B∩(C∪~C)

⇒ A∩E ⊆ B∩E

⇒ A ⊆ B

## 命题演算法证明 X=Y

任取 x，
 x∈X ⇒ ... ⇒ x∈Y
 x∈Y ⇒ ... ⇒ x∈X
 或者
 x∈X ⇔ ... ⇔ x∈Y

例8 证明 A∪(A∩B)=A （吸收律）

证 任取 x，

x∈A∪(A∩B) ⇔ x∈A ∨ x∈A∩B

⇔ x∈A ∨ (x∈A ∧ x∈B) ⇔ x∈A

## 等式替换证明X=Y

不断进行代入化简，最终得到两边相等

例9 证明 A∪(A∩B)=A （吸收律）

证 （假设交换律、分配律、同一律、零律成立）

A∪(A∩B)

=(A∩E)∪(A∩B)      同一律

=A∩(E∪B)      分配律

=A∩(B∪E)      交换律

=A∩E      零律

=A      同一律

## 反证法证明X=Y

假设 X=Y 不成立，则存在 x 使得 x∈X 且 x∉Y，或者存在 x 使得 x∈Y 且 x∉X，然后推出矛盾。

## 例10 证明以下等价条件

A⊆B ⇔ A∪B=B ⇔ A∩B=A ⇔ A−B=∅
(1)      (2)      (3)      (4)

证明顺序：

(1) ⇒(2), (2) ⇒(3), (3) ⇒(4), (4) ⇒(1)

(1) ⇒ (2)

显然 $B \subseteq A \cup B$，下面证明 $A \cup B \subseteq B$。

任取 $x$，

$x \in A \cup B \Leftrightarrow x \in A \lor x \in B \Rightarrow x \in B \lor x \in B \Leftrightarrow x \in B$

因此有 $A \cup B \subseteq B$。综合上述（2）得证。

(2) ⇒ (3)

$A = A \cap (A \cup B) \Rightarrow A = A \cap B$

（将 $A \cup B$ 用 $B$ 代入）

(3) ⇒(4)
假设 A−B≠∅, 即 ∃x∈A−B, 那么 x∈A 且 x∉B. 而
x∉B ⇒ x∉A∩B.
从而与 A∩B=A 矛盾.

(4) ⇒(1)
假设 A⊆B 不成立, 那么
∃x (x∈A ∧ x∉B) ⇒ x∈A−B ⇒ A−B≠∅
与条件（4）矛盾.

## 集合运算法证明 X=Y

由已知等式通过运算产生新的等式
X=Y ⇒ X∩Z=Y∩Z, X∪Z=Y∪Z, X-Z=Y-Z

例11 证明 A∩C=B∩C ∧ A∪C=B∪C ⇒ A=B

证 由 A∩C=B∩C 和 A∪C=B∪C 得到

(A∪C)-(A∩C)=(B∪C)-(B∩C)

从而有 A⊕C=B⊕C

因此

A⊕C=B⊕C ⇒ (A⊕C)⊕C=(B⊕C)⊕C

⇒ A⊕(C⊕C)=B⊕(C⊕C) ⇒ A⊕∅=B⊕∅ ⇒ A=B

## 3.3 集合中元素的计数

- 集合的基数与有穷集合
- 包含排斥原理
- 有穷集的计数

## 集合的基数与有穷集合

集合 A 的基数: 集合A中的元素数, 记作 cardA

有穷集 A: cardA=|A|=n, n为自然数.

有穷集的实例:

A={ a,b,c}, cardA=|A|=3;

B={ x | x²+1=0, x∈R}, cardB=|B|=0

无穷集的实例:

N, Z, Q, R, C 等

## 包含排斥原理

定理 设 S 为有穷集，P₁, P₂, ..., Pₘ 是 m 种性质，Aᵢ 是 S 中具有性质 Pᵢ 的元素构成的子集，i=1, 2, ..., m. 则 S 中不具有性质 P₁, P₂, ..., Pₘ 的元素数为

|Ā₁ ∩ Ā₂ ∩ ... ∩ Āₘ|
= |S| - Σᵢ₌₁ᵐ |Aᵢ| + Σ₁≤i<j≤m |Aᵢ ∩ Aⱼ| - Σ₁≤i<j<k≤m |Aᵢ ∩ Aⱼ ∩ Aₖ| + ...
+ (-1)ᵐ |A₁ ∩ A₂ ∩ ... ∩ Aₘ|

## 证明

证明要点：任何元素 x，如果不具有任何性质，则对等式右边计数贡献为 1，否则为 0

证 设 x 不具有性质 P₁, P₂, ..., Pₘ,
    x ∉ Aᵢ, i = 1, 2, ..., m
    x ∉ Aᵢ ∩ Aⱼ, 1 ≤ i < j ≤ m
    ...
    x ∉ A₁ ∩ A₂ ∩ ... ∩ Aₘ,
    x 对右边计数贡献为
    1 − 0 + 0 − 0 + ... + (−1)ᵐ · 0 = 1

## 证明（续）

设 $x$ 具有 $n$ 条性质，$1\le n\le m$

- $x$ 对 $|S|$ 贡献为 $1$
- $x$ 对 $\sum_{i=1}^{m}|A_i|$ 贡献为 $C_n^1$
- $x$ 对 $\sum_{1\le i<j\le m}|A_i\cap A_j|$ 贡献为 $C_n^2$
- ⋯⋯
- $x$ 对 $|A_1\cap A_2\cap\cdots\cap A_m|$ 贡献为 $C_n^m$

$x$ 对右边计数贡献为

$$1-C_n^1+C_n^2-\cdots+(-1)^mC_n^m=\sum_{i=0}^{n}C_n^i=0$$

## 推论

S中至少具有一条性质的元素数为

$$\left|A_1\cup A_2\cup\cdots\cup A_m\right|$$

$$=\sum_{i=1}^{m}|A_i|-\sum_{1\le i<j\le m}|A_i\cap A_j|+\sum_{1\le i<j<k\le m}|A_i\cap A_j\cap A_k|+\cdots$$

$$+(-1)^{m-1}|A_1\cap A_2\cap\cdots\cap A_m|$$

证明

$$\left|A_1\cup A_2\cup\cdots\cup A_m\right|$$

$$=|S|-|\overline{A_1\cup A_2\cup\cdots\cup A_m}|$$

$$=|S|-|\overline{A_1}\cap\overline{A_2}\cap\cdots\cap\overline{A_m}|$$

将定理 1 代入即可

## 应用

例1 求1到1000之间（包含1和1000在内）既不能被 5 和6 整除，也不能被 8 整除的数有多少个？

解： S = { x | x∈Z, 1 ≤ x ≤1000 },
如下定义 S 的 3 个子集 A, B, C:

A = { x | x∈S, 5 | x },

B = { x | x∈S, 6 | x },

C = { x | x∈S, 8 | x }

## 例1（续）

对上述子集计数：

$|S|=1000,$

$|A|=\lfloor1000/5\rfloor=200,\quad |B|=\lfloor1000/6\rfloor=133,$

$|C|=\lfloor1000/8\rfloor=125,$

$|A\cap B|=\lfloor1000/30\rfloor=33,\quad |B\cap C|=\lfloor1000/40\rfloor=25,$

$|A\cap C|=\lfloor1000/40\rfloor=25,$

$|A\cap C|=\lfloor1000/24\rfloor=41,$

$|A\cap B\cap C|=\lfloor1000/120\rfloor=8,$

代入公式

$N=1000-(200+133+125)+(33+25+41)-8=600$

## 文氏图法

求1到1000之间（包含1和1000在内）既不能被5和6整除，也不能被8整除的数有多少个？

![](img/3e54617849435b84ab04e6656729f806_179_0.png)
