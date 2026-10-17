
- (4) 设\(M_n(\mathbf{R})\)表示所有\(n\)阶（\(n\geqslant 2\)）实矩阵的集合，即

\[
M_n(\mathbf{R})=\left\{\left[\begin{array}{cccc}
a_{11} & a_{12} & \cdots & a_{1n} \\
a_{21} & a_{22} & \cdots & a_{2n} \\
\cdots & & & \\
a_{n1} & a_{n2} & \cdots & a_{nn}
\end{array}\right] \;\middle|\; a_{ij}\in\mathbf{R},\ i,j=1,2,\dots,n\right\}
\]

则矩阵加法和乘法都是\(M_n(\mathbf{R})\)上的二元运算。

- (5) \(S\)为任意集合，则\(\cup\)、\(\cap\)、\(\sim\)、\(\oplus\)为\(P(S)\)上二元运算。

- (6) \(S^S\)为\(S\)上的所有函数的集合，则合成运算\(\circ\)为\(S^S\)上二元运算。

### 二元运算

定理：设\(*\)是集合\(X\)中的二元运算，且\(S_1 \subseteq X\)和\(S_2 \subseteq X\)。在\(*\)运算的作用下，\(S_1\)和\(S_2\)都是封闭的。于是在\(*\)运算的作用下\(S_1 \cap S_2\)也是封闭的。

证：因为\(S_1\)和\(S_2\)在运算\(*\)的作用下是封闭的，所以对于每一个序偶\(\langle x_1, x_2 \rangle \in S_1\)来说，有\(x_1 * x_2 \in S_1\)；对于每一个序偶\(\langle x_1, x_2 \rangle \in S_2\)来说有\(x_1 * x_2 \in S_2\)。因此，对于每一个序偶\(\langle x_1, x_2 \rangle \in S_1 \cap S_2\)来说，有\(x_1 * x_2 \in S_1 \cap S_2\)。

### 一元运算的定义与实例

定义9.2 设\(S\)为集合，函数\(f:S\to S\)称为\(S\)上的一元运算（Unary Operation），简称一元运算。

例2

- (1) 求相反数是整数集合\(\mathbb{Z}\)，有理数集合\(\mathbb{Q}\)和实数集合\(\mathbb{R}\)上的一元运算
- (2) 求倒数是非零有理数集合\(\mathbb{Q}^*\)，非零实数集合\(\mathbb{R}^*\)上一元运算
- (3) 求共轭复数是复数集合\(\mathbb{C}\)上的一元运算
- (4) 在幂集\(P(S)\)上规定全集为\(S\)，则求绝对补运算\(\sim\)是\(P(S)\)上的一元运算。
- (5) 设\(S\)为集合，令\(A\)为\(S\)上所有双射函数的集合，\(A\subseteq S^S\)，求一个双射函数的反函数为\(A\)上的一元运算。
- (6) 在\(n(n\geq2)\)阶实矩阵的集合\(M_n(\mathbb{R})\)上，求转置矩阵是\(M_n(\mathbb{R})\)上的一元运算。

## 二元与一元运算的表示

### 1. 算符

可以用\(\circ, *, \cdot, \oplus, \otimes, \triangle\)等符号表示二元或一元运算，称为算符。对二元运算\(\circ\)，如果\(x\)与\(y\)运算得到\(z\)，记做\(x \circ y = z\)。而二元运算符习惯于前置、中置或后置，如：\(+xy\)，\(x+y\)，\(xy+\)。对一元运算\(\triangle\)，\(x\)的运算结果记作\(\triangle x\)。

### 2. 表示二元或一元运算的方法：解析公式和运算表

### 公式表示

例 设\(\mathbb{R}\)为实数集合，如下定义\(\mathbb{R}\)上的二元运算\(*\)：

\[
\forall x,y\in\mathbb{R},\quad x*y=x.
\]

那么\(3*4=3\)，\(0.5*(-3)=0.5\)。

### 运算表：表示有穷集上的一元和二元运算

二元运算的运算表：

| \(\circ\) | \(a_1\) | \(a_2\) | \(\cdots\) | \(a_n\) |
|---|---|---|---|---|
| \(a_1\) | \(a_1\circ a_1\) | \(a_1\circ a_2\) | \(\cdots\) | \(a_1\circ a_n\) |
| \(a_2\) | \(a_2\circ a_1\) | \(a_2\circ a_2\) | \(\cdots\) | \(a_2\circ a_n\) |
| \(\cdots\) | \(\cdots\) | \(\cdots\) | \(\cdots\) | \(\cdots\) |
| \(a_n\) | \(a_n\circ a_1\) | \(a_n\circ a_2\) | \(\cdots\) | \(a_n\circ a_n\) |

一元运算的运算表：

|   | \(o(a_i)\) |
|---|---|
| \(a_1\) | \(o(a_1)\) |
| \(a_2\) | \(o(a_2)\) |
| \(\cdots\) | \(\cdots\) |
| \(a_n\) | \(o(a_n)\) |

例3 设\(S=P(\{a,b\})\)，\(S\)上的\(\oplus\)和\(\sim\)运算的运算表如下。

\(\oplus\)运算的运算表：

| \(\oplus\) | \(\varnothing\) | \(\{a\}\) | \(\{b\}\) | \(\{a,b\}\) |
|---|---|---|---|---|
| \(\varnothing\) | \(\varnothing\) | \(\{a\}\) | \(\{b\}\) | \(\{a,b\}\) |
| \(\{a\}\) | \(\{a\}\) | \(\varnothing\) | \(\{a,b\}\) | \(\{b\}\) |
| \(\{b\}\) | \(\{b\}\) | \(\{a,b\}\) | \(\varnothing\) | \(\{a\}\) |
| \(\{a,b\}\) | \(\{a,b\}\) | \(\{b\}\) | \(\{a\}\) | \(\varnothing\) |

\(\sim\)运算的运算表：

| \(x\) | \(\sim x\) |
|---|---|
| \(\varnothing\) | \(\{a,b\}\) |
| \(\{a\}\) | \(\{b\}\) |
| \(\{b\}\) | \(\{a\}\) |
| \(\{a,b\}\) | \(\varnothing\) |

### 二元运算的性质

定义9.3 设\(\circ\)为\(S\)上的二元运算，

- (1) 若对任意\(x, y \in S\)有\(x \circ y = y \circ x\)，则称运算在\(S\)上满足**交换律**。
- (2) 若对任意\(x, y, z \in S\)有\((x \circ y) \circ z = x \circ (y \circ z)\)，则称运算在\(S\)上满足**结合律**。
- (3) 若对任意\(x \in S\)有\(x \circ x = x\)，则称运算在\(S\)上满足**幂等律**。

定义9.4 设\(\circ\)和\(*\)为\(S\)上两个不同的二元运算，

- (1) 若对任意\(x, y, z \in S\)有  
\((x * y) \circ z = (x \circ z) * (y \circ z)\)，  
\(z \circ (x * y) = (z \circ x) * (z \circ y)\)，  
则称\(\circ\)运算对\(*\)运算满足**分配律**。
- (2) 若\(\circ\)和\(*\)都可交换，且对任意\(x, y \in S\)有  
\(x \circ (x * y) = x\)，  
\(x * (x \circ y) = x\)，  
则称\(\circ\)和\(*\)运算满足**吸收律**。

### 前置式表示

前置式可交换的二元运算\(f : X \times X \to X\)可表达成：对于每一个\(x, y \in X\)有\(f\langle x, y \rangle = f\langle y, x \rangle\)；可结合的二元运算可表达成：对于每一个\(x, y, z \in X\)有\(f\langle f\langle x, y \rangle, z \rangle = f\langle x, f\langle y, z \rangle \rangle\)；对于运算\(g : X \times X \to X\)是可分配的二元运算，\(f : X \times X \to X\)可表达成\(f\langle x, g\langle y, z \rangle \rangle = g\langle f\langle x, y \rangle, f\langle x, z \rangle \rangle\)。

\(\mathbb{Z},\mathbb{Q},\mathbb{R}\)分别为整数、有理数、实数集；\(M_n(\mathbb{R})\)为\(n\)阶实矩阵集合，\(n\geqslant 2\)；\(P(B)\)为幂集；\(A^A\)为从\(A\)到\(A\)的函数集，\(|A|\geqslant 2\)。

| 集合 | 运算 | 交换律 | 结合律 | 幂等律 |
|---|---|---|---|---|
| \(\mathbb{Z},\mathbb{Q},\mathbb{R}\) | 普通加法\(+\)，普通乘法\(\times\) | 有，有 | 有，有 | 无，无 |
| \(M_n(\mathbb{R})\) | 矩阵加法\(+\)，矩阵乘法\(\times\) | 有，无 | 有，有 | 无，无 |
| \(P(B)\) | 并\(\cup\)，交\(\cap\)，相对补\(-\)，对称差\(\oplus\) | 有，有，无，有 | 有，有，无，有 | 有，有，无，无 |
| \(A^A\) | 函数复合\(\circ\) | 无 | 有 | 无 |

## 实例

\(\mathbb{Z},\mathbb{Q},\mathbb{R}\)分别为整数、有理数、实数集；\(M_n(\mathbb{R})\)为\(n\)阶实矩阵集合，\(n\geqslant 2\)；\(P(B)\)为幂集；\(A^A\)为从\(A\)到\(A\)的函数集，\(|A|\geqslant 2\)。

| 集合 | 运算 | 分配律 | 吸收律 |
|---|---|---|---|
| \(\mathbb{Z},\mathbb{Q},\mathbb{R}\) | 普通加法\(+\)与乘法\(\times\) | \(\times\)对\(+\)可分配；\(+\)对\(\times\)不分配 | 无 |
| \(M_n(\mathbb{R})\) | 矩阵加法\(+\)与乘法\(\times\) | \(\times\)对\(+\)可分配；\(+\)对\(\times\)不分配 | 无 |
| \(P(B)\) | 并\(\cup\)与交\(\cap\) | \(\cup\)对\(\cap\)可分配；\(\cap\)对\(\cup\)可分配 | 有 |
|  | 交\(\cap\)与对称差\(\oplus\) | \(\cap\)对\(\oplus\)可分配 | 无 |
