
![](img/5123c27d7478faaa822d0f1f02fc503f_1805_0.png)

**定义9.5**

(1) 对任何集合A，其所含元素的量称为A的基数(势)，记为Card A。等势的集合有相同的基数(势)；

(2) 对于有限集A，A的基数(势)定义为它所含元素的个数；

(3) 对于无限可数集A，其基数(势)用ℵ₀表示，即Card A=ℵ₀

(4) 所有与实数集合 R 等势的集合A，其基数 (势) 用ℵ表示，即 Card A= ℵ.

注：自然数集N及与N等势的一切集合的基数都为ℵ₀，特别地，

Card Z = Card Q = Card N × N = Card N = ℵ₀；

Card P(N) = Card {0,1}^N = Card [a,b] = Card (a,b) = Card R = ℵ；

Card P(A) = Card {0,1}^A.

**定义9.6** 设 \(A,B\) 为集合，若从 \(A\) 到 \(B\) 有一个单射，则称 \(Card\ A\leq Card\ B\)，即：

\[
Card\ A\leq Card\ B\Leftrightarrow A\preceq B;
\]

若 \(Card\ A\leq Card\ B\) 且 \(Card\ A\neq Card\ B\)，则称

\[
Card\ A<Card\ B
\]

**定理9.7**

(1) 对任何有限集 \(A\)，\(Card\ A<\aleph_0\)

(2) 对任何无限集 \(A\)，\(\aleph_0<Card\ A\)

(3) \(\aleph_0<\aleph\)

**证：** (1) 设 \(Card\ A=n\)，则 \(A\approx\{0,1,2,\ldots,n-1\}\)。定义函数

\[
f:\{0,1,2,\ldots,n-1\}\to N,
\]

\[
f(x)=x。
\]

则 \(f\) 是单射，故 \(Card\ A\leq\aleph_0\)。

另一方面，设 \(g\) 是任意一个从 \(\{0,1,2,\ldots,n-1\}\) 到 \(N\) 的函数，记

\[
k=1+\max\{g(0),g(1),\ldots,g(n-1)\}
\]

则 \(k\in N\)，但对 \(\forall x\in\{0,1,2,\ldots,n-1\}\)，\(g(x)\neq k\)，即 \(k\) 在 \(g\) 下无原像，故 \(g\) 不是满射。由 \(g\) 的任意性，不存在从 \(\{0,1,2,\ldots,n-1\}\) 到 \(N\) 的满射，故

\[
Card\ A\neq\aleph_0，
\]

从而

\[
Card\ A<\aleph_0。
\]

(2) 对任何无限集 $A$，$\aleph_0 \leq \operatorname{Card} A$；

因 $A$ 是无限集，故 $A$ 包含无限可数子集 $A'$。构造函数
$$f:A'\to A,\quad f(x)=x.\quad(\forall x\in A').$$
则 $f$ 是从 $A'$ 到 $A$ 的单射，故 $\operatorname{Card} A'\leq \operatorname{Card} A$。
但 $\operatorname{Card} A'=\aleph_0$，从而 $\aleph_0\leq \operatorname{Card} A$。

(3) $\aleph_0\leq\aleph$。

构造从 $\mathbb{N}$ 到 $[0,1]$ 的函数 $f:\mathbb{N}\to[0,1]$，$f(n)=\frac{1}{n+1}$。
则 $f$ 是单射，故 $\aleph_0=\operatorname{Card}\mathbb{N}\leq\operatorname{Card}[0,1]=\aleph$。
故 $\aleph_0\leq\aleph$。
另一方面，由定理 9.2，$\mathbb{N}\not\approx\mathbb{R}$。故 $\aleph_0<\aleph$。

**注：** 定理9.7说明：

（1）任何有限集的基数都小于\(\aleph_0\)；\(\aleph_0\)是无穷集合的最小基数；\(\aleph\)是比\(\aleph_0\)更大的基数；

（2）已知的基数由小到大排列为：\(0,1,2,\cdots,\aleph_0,\aleph,\cdots\)。

- **连续统假设：**不存在集合\(A\)，使得\(\aleph_0<Card\ A<\aleph\)。

**定理9.8（Cantor定理）** 设\(A\)是集合，则\(Card\ A<Card\ \mathrm{P}(A)\)。

**证明：** 构造函数\(f:A\to\mathrm{P}(A)\)，\(f(x)=\{x\}\)，（\(\forall x\in A\)）。

易见\(f\)是一个单射，故\(Card\ A\leq Card\ \mathrm{P}(A)\)；

另一方面，由定理9.2，\(A\not\approx \mathrm{P}(A)\)，故

\[Card\ A<Card\ \mathrm{P}(A)。\]

**注：** 由Cantor定理知，不存在最大的基数。

**例9.4** 求下列集合的基数：

(1) T={x|x是单词 “baseball”中的字母}

(2) B={x|x∈R∧x²=9∧2x=8}

(3) C=P(A), A={1,3,7,11}

解： (1)∵ T={b, a, s, e, l}， 故 Card T = |T| = 5。

(2)∵ B=Φ， 故 Card B = 0。

(3)∵ |A|=4， 故 Card C = Card P(A)= |P(A)| = 2⁴=16。

**例9.5** 设 $A、B$ 为集合，且 $Card\,A=\aleph_0$，$Card\,B=n$，$(n\ne0$ 是自然数$)$。求 $Card(A\times B)$。

**解法1：** 令 $A=\{a_0,a_1,\ldots\}$，$B=\{b_0,b_1,\ldots,b_{n-1}\}$。

对 $\langle a_i,b_j\rangle\in A\times B$ 和 $\langle a_k,b_l\rangle\in A\times B$，有

$\langle a_i,b_j\rangle=\langle a_k,b_l\rangle\Longleftrightarrow(a_i=a_k)\land(b_j=b_l)\Longleftrightarrow(i=k)\land(j=l)$。

定义 $f:A\times B\to\mathbb{N}$，$f(\langle a_i,b_j\rangle)=i\cdot n+j$，$(i=0,1,\ldots；j=0,1,\ldots,n-1)$。

则可以检验 $f$ 是 $A\times B$ 到 $\mathbb{N}$ 的双射函数，故

$$Card(A\times B)=Card\,\mathbb{N}=\aleph_0.$$

**解法2：** 因 $A$ 和 $B$ 都是可数集，由定理9.6，两个可数集的笛卡尔集仍是可数集，故

$$Card(A\times B)=\aleph_0.$$

## 9 布尔代数（Boolean Algebra）

竺可桢学院的同学们，新年好！

我非常珍视这个学期与大家一起学习离散数学的美好时光。你们的聪明才智与勤于钻研的精神给我留下深刻的印象，在此新春之际，祝大家新年愉快，取得好的学习成绩，并拥有美好灿烂的明天！

同时，我以我们浙江大学计算机图形图像实验室的名义热情地邀请你们中有兴趣的同学选择专业及实验室的时候加入我们的实验室，我们实验室的简介也与这次讲义放在一起，文件名是《计算机学院图形图像实验室的简介》，请有兴趣的同学浏览，仅供参考。

浙江大学计算机学院  张三元

Email: syzhang@cs.zju.edu.cn

Tel: 87952690 地址：玉泉校区曹光彪楼东楼310

### 9.1 代数系统和群

#### 9.1.1 二元运算及性质

二元运算是最常见的代数运算，例如：实数的加法、减法、乘法，集合的交、并等运算都是二元运算。

**定义9.1** 设A为任意非空集合，函数\(f: A \times A \rightarrow A\)称为集合A上的一个二元运算。

**例9.1** (1) 设𝑍为整数集，定义𝑍上的“⊙”运算为普通的加法“+”，即：a⊙b=a+b。则：“+”是𝑍上的二元运算。同样𝑍上的普通减法、乘法运算也是二元运算。

(2) 在非零实数集𝑅*上定义的普通乘法和除法是𝑅*上的二元运算。但一般的加法和减法并不是二元运算。因为1+(-1)=0∉𝑅*，1−1=0∉𝑅*，𝑅*对一般的加法和减法是不封闭的，因此不是𝑅*上的二元运算。

**例9.2** 设A=𝑍⁺，定义：

(1) a⊙₁b=a−b，则：“⊙₁”不是𝑍⁺上的二元运算。因为“⊙₁”在𝑍⁺中是不封闭的。例如：1⊙₁3=−2∉𝑍⁺。

(2) a⊙₂b=a÷b，则：“⊙₂”不是𝑍⁺上的二元运算。因为“⊙₂”在𝑍⁺中是不封闭的。例如：1⊙₂2=0.5∉𝑍⁺。

(3) a⊙₃b=a×b，则：“⊙₃”是𝑍⁺上的二元运算。

**注：** 红色“∈”表示不属于
