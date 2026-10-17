

# 【定理4】：传递闭包 $R^*$ 一定是传递的。

证明：设 $(a,b)$、$(b,c)\in R^*$，则存在 $i,j$，使 $(a,b)\in R^i$，$(c,b)\in R^j$，故 $(a,b)\in R^{(i+j)}\subseteq R^*$。

# 传递扩张的实际意义：

例：
$R=\{(a,b)\mid a与b是父子关系\}$
$R\cdot R=\{(a,b)\mid a与b是祖孙关系\}$
$R_1=\{(a,b)\mid a与b是三代以内男性直系亲属\}$
…

# Relations关系

【定理5】：设 $|A|=n$，$R$ 是 $A$ 上二元关系，则存在正整数 $k$，$k\le n$，使 $R^*=R\cup R^2\cup\cdots\cup R^k$。

# 证明：

对∀（x，y）∈R*，∃k，使（x，y）∈R^k，表明在A中存在不同元素a₁，a₂，…，aₖ₋₁，使（x，a₁），（a₁，a₂），（a₂，a₃），…，（aₖ₋₁，y）∈R。

若k>n，由鸽洞原理，则a₁，a₂，…，aₖ₋₁，y中至少有两个相同，不妨设aᵢ=y，（i≤k−1）。

于是 $(x, a_1), \ldots (a_i, a_{i-1}) \in R,$

$(a_{i-1}, y) \in R,$

故 $(x, y) \in R^i,$

即 若 $k>n$，必存在比 $k$ 的正整数 $i$，使 $(x, y) \in R^i$。

**注：**

定理说明，可用 $R \cup R^2 \cup \ldots \cup R^n$ 来求 $R^*$。

**例 6：**

设 $A=\{1,\ 2,\ 3\}$，

$R=\{(1,1),\ (1,2),\ (2,3)\}$

求 $R^*$。

# Relations关系

解：
\( R = \begin{bmatrix} 1 & 1 & 0 \\ 0 & 0 & 1 \\ 0 & 0 & 0 \end{bmatrix}, \quad R^2 = \begin{bmatrix} 1 & 1 & 1 \\ 0 & 0 & 0 \\ 0 & 0 & 0 \end{bmatrix} = R^3 \)

故
\( R^* = R \cup R^2 \cup R^3 = \begin{bmatrix} 1 & 1 & 1 \\ 0 & 0 & 1 \\ 0 & 0 & 0 \end{bmatrix} \)

\( R^* = \{ (1, 1), (1, 2), (1, 3), (2, 3) \} \)

# Relations关系

注：当 | A | = n较大时，用定理5计算 R* 工作量非常大。

Warshall算法：(1962) 设R是n个元素集合上的二元关系 (1)是R的相关矩阵； (2) i ← 1； (3) for j = 1 to n do if a<sub>j,i</sub> = 1 then do for k = 1 to n do a<sub>j,k</sub> ← a<sub>j,k</sub> ∨ a<sub>i,k</sub> (4) i = i + 1； (5) if i ≤ n, then go (3) else stop

注：（1）结果 \((a_{ij})_{n\times n}\) 是 \(R^*\) 的相关矩阵。
（2）算法的复杂度为 \(n^3\)。

例7：\(A=\{a,b,c,d\}\)
\(R=\{(a,b),(b,c),(c,d)\}\)

计算 \(R^*\)。

# Relations关系

\( R = \begin{bmatrix} 0 & 1 & 0 & 0 \\ 0 & 0 & 1 & 0 \\ 0 & 0 & 0 & 1 \\ 0 & 0 & 0 & 0 \end{bmatrix} \)

(1) i=1  由于 \( a_{j1}=0 (j=1,2,3,4) \) 不改动

(2) i=2  \( j=1, \ a_{ji}=1 \Rightarrow a_{13}=1 \)

(3) i=3  \(\begin{bmatrix} 0 & 1 & 1 & 0 \\ 0 & 0 & 1 & 0 \\ 0 & 0 & 0 & 1 \\ 0 & 0 & 0 & 0 \end{bmatrix}\)

# Relations关系

j=1， a13=1 ⇒ a14=1

j=2， a23=1 ⇒ a24=1

即

$R^* = \{(a,b),(a,c),(a,d),(b,c),(b,d),(c,d)\}$

# 小结

+   (1) 二元关系的集合运算

+   (2) 二元关系的函数运算

+   (3) 二元关系的闭包运算

# 进一步的思考

+   1、从原有二元关系形成新的二元关系
+   2、现有的二元关系的进一步归纳

# 练习

pp. 382　　3、25

pp. 407　　29

# 5.3 等价关系 Equivalence Relations

## [定义1] 等价关系：
A 上的二元关系 R，如果 R 是

(1) 自反的  
(2) 对称的  
(3) 传递的  

称 R 为等价关系/Equivalence Relations。

# Relations关系

example1: 52张扑克牌中的同花关系

example2: 52张扑克牌中的同点关系

# example 4: Congruence Modulo m

R={ (a, b) | a ≡ b (mod m) }

# Relations关系

例（M=3）：
\[
R=\{(a,b)\mid a\equiv b\pmod{3},\ a,b\in I\}
\]
是整数集合 I 上模 3 同余的二元关系。
证明 R 是等价关系。

证明：由于 $3\mid(a-b)$ 等价于 $a\equiv b\pmod{3}$

+   1. $3\mid(a-a)$，自反性

+   2. 若 $3\mid(a-b)$，则 $3\mid(b-a)$，对称性

+   3. 若 $3\mid(a-b)$，$3\mid(b-c)$，则
+      $a-c=(a-b)+(b-c)$
+      $\Rightarrow 3\mid(a-c)$
+      满足传递性，故 $R$ 是等价关系

# example 4: Congruence Modulo m

R={ (a, b) | a ≡ b (mod m) }

m=3时， 3个等价类： [0]， [1]， [2]

其中  [ 0 ] = { ..., −6 , −3 , 0 , 3 , 6 , ...}  [ 1 ] = { ..., −5 , −2 , 1 , 4 , 7 , ...}  [ 2 ] = { ..., −4 , −1 , 2 , 5 , 8 , ...}

# Relations关系

【定理1】 R是集合A上的一个等价关系，则下列命题是等价的：

+   1、(a, b) ∈ R
+   2、[a] = [b]
+   3、[a] ∩ [b] ≠ ∅

# Relations关系

## 注：

等价关系 R 把 A 的元素分为若干类，各类之间没有公共元素。确定的 R 是对集合 A 进行的一个划分。

## [定义3]集合的划分：把集合 A 分为若干子集 A₁，A₂，...，满足：

+   (1) 当 i ≠ j 时 Aᵢ ∩ Aⱼ = Φ

+   (2) ∀ a ∈ A， ∃ i，使 a ∈ Aᵢ （i = 1，2，...）

则集合 Pᵣ（A）= { A₁，A₂，...，Aₙ，... } 称为 A 的一个划分/分划/partition。

# 定理2：

A 在等价关系 R 下的等价类是 A 的一个划分。对于 A 的任何一个划分，也必有 A 上的一个等价关系 R 与之对应。

# Relations关系

## 证明：

R是等价关系， ∀ a ∈ A， 由 R 的自反性，
( a， a ) ∈ R，即 a 与 a 属于同一等价类，也
即 ∃ i， a ∈ A<sub>i</sub>

若 i ≠ j， A<sub>i</sub>≠A<sub>j</sub>，而 A<sub>i</sub>∩A<sub>j</sub>≠Φ，则 ∃ c ∈ A
<sub>i</sub>∩A<sub>j</sub>， c ∈ A<sub>i</sub>，且 c ∈ A<sub>j</sub>，

对 ∀ a ∈ A<sub>i</sub>， a ~ c

对 ∀ b ∈ A<sub>j</sub>， b ~ c，即 c ~ b (对称性)

由 R 传递性， a ~ b

由 a， b 的任意性，故 A<sub>i</sub> = A<sub>j</sub>

