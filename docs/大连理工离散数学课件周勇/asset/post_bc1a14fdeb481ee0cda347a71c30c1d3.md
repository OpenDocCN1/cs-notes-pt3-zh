

## 偏序关系

通常用符号“≤”表示偏序。这样，符号≤就不单纯意味着实数中的“小于或等于”关系。事实上，这是从特定情况中，借用符号≤去表示更为普遍的偏序关系。对于偏序关系来说，如果有 且\(x \leq y\)，则按不同情况称它是“小于或等于”，“包含”，“在之前”等等。

如果\(R\)是集合\(P\)中的偏序关系，则 \(\widetilde{R}\)也是\(P\)中的偏序关系。如上所述，如果用\(\leq\)表示\(R\)，则用\(\geq\)表示 \(\widetilde{R}\)。如果\(<P, \leq>\)是一个偏序集合，则\(<P, \geq>\)也是一个偏序集合，称\(<P, \geq>\)是\(<P, \leq>\)的对偶。

例：设\(R\)是实数集合。“小于或等于”关系是\(R\)中的偏序关系；这个关系的逆关系“大于或等于”关系也是\(R\)中的偏序关系。

例：设\(P(A)=X\)是\(A\)的幂集。\(X\)中的包含关系\(\subseteq\) 是个偏序关系；这个关系的逆关系\(\supseteq\) 也是个偏序关系。

设\(\mathbf{Z}_+\)是正整数集合，且\(x,y,z \in \mathbf{Z}_+\),当且仅当存在\(z\)，能使\(xz=y\)，才有“\(x\)整除\(y\)”(可写成\(x|y\))，换言之，“\(y\)是\(x\)的整倍数”。“整除”和“整倍数”互为逆关系，它们都是\(\mathbf{Z}_+\)中的偏序关系。

例：设 $Z_+={2,3,6,8}$，$\leq$ 是 $Z_+$ 中的“整除”关系。试表达出“整除”和“整倍数”关系。

解：“整除”关系 $\leq$ 为

$\leq=\{\langle2,2\rangle,\langle3,3\rangle,\langle6,6\rangle,\langle8,8\rangle,\langle2,6\rangle,\langle2,8\rangle,\langle3,6\rangle\}$

“整倍数”关系是 $\geq$

$\geq=\{\langle2,2\rangle,\langle3,3\rangle,\langle6,6\rangle,\langle8,8\rangle,\langle6,2\rangle,\langle8,2\rangle,\langle6,3\rangle\}$

实数集合 $R$ 中的“小于”关系 $<$ 和“大于”关系 $>$，都不是偏序关系，因为它们都不是自反的。但它们是实数集合中的另一种关系——拟序关系。

## 拟序关系

拟序关系和偏序关系的关系：

定理：设 $R$ 是集合中的二元关系。于是可有

- (a) 如果 $R$ 是个拟序关系，则 $r(R)=R\cup I_x$ 是一个偏序关系。

- (b) 如果 $R$ 是个偏序关系，则 $R-I_x$ 是个拟序关系。

## 全序关系

定义：设 \(\langle P,\leq\rangle\) 是个偏序集合。如果对于每一个 \(x,y\in P\)，或者 \(x\leq y\) 或者 \(y\leq x\)，亦即

\[(\forall x)(\forall y)(x\in P\land y\in P\to x\leq y\lor y\leq x)\]

则称偏序关系\(\leq\)是**全序关系**，简称**全序**，序偶 \(\langle P,\leq\rangle\) 称为**全序集合**。

注意：\(P\)中具有全序关系的各元素，总能按线性次序 \(x_1,x_2,\cdots\) 排列起来，这里当且仅当 \(i\leq j\)，才有 \(x_i\leq x_j\)，故全序也称为简单序或线性序，因此，序偶 \(\langle P,\leq\rangle\) 在这种情况下也被称为**线性序集**或**链**。

### 元素的可比性：

设\(\le\)是集合\(P\)中的偏序关系。对于 \(x,y \in P\)，如果有  
\(x \le y\) 或 \(y \le x\)，则\(P\)中的元素\(x\)和\(y\)称为**可比的**。在偏序集合中，并非任何两个元素\(x\)和\(y\)都存在有\(x \le y\) 或 \(y \le x\)的关系。事实上，对于某些\(x\)和\(y\)来说，和可能没有关系。在这种情况下，称\(x\)和\(y\)是**不可比的**。正是由于这种原因，才称作“偏”序关系。在全序集合中，任何两个元素都是可比的。

例：设\(R\)是实数集合，\(a\)和\(b\)是\(R\)的元素。对于每一个实数\(a\)，设\(S_a = \{x \mid 0 \leq x < a\}\)和\(S\)是集合并且\(S = \{S_a \mid a \geq 0\}\)。如果\(a < b\)，则\(S_a \subseteq S_b\)，因此\(\langle S, \subseteq \rangle\)是一个全序集合。

如果\(A\)是个含有多于一个元素的集合，则\(\langle P(A), \subseteq \rangle\)不是一个全序集合。

例如，设\(A = \{a, b, c\}\)，\(P(A) = \{\varnothing, \{a\}, \{b\}, \{c\}, \{a, c\}, \{b, c\}, \{a, b, c\}\}\)在\(P(A)\)上定义一个包含关系 \(\subseteq\)，可以看出\(\{a\}\)和\(\{b, c\}\)，\(\{a, b\}\)和\(\{a, c\}\)等等都是不可比的。

## 字母次序关系

定义：设 \( R \) 是实数集合且 \( P = R \times R \)。假定 \( R \) 中的关系 \( \geq \) 是一般的“大于或等于”关系。对于 \( P \) 中的任何两个序偶 \( \langle x_1, y_1 \rangle \) 和 \( \langle x_2, y_2 \rangle \)，可以定义一个关系 \( S \)

\( \langle x_1, y_1 \rangle S \langle x_2, y_2 \rangle \iff (x_1 > x_2) \lor (x_1 = x_2 \land y_1 \geq y_2) \)

如果 \( \langle x_1, y_1 \rangle \not S \langle x_2, y_2 \rangle \)，则有 \( \langle x_2, y_2 \rangle S \langle x_1, y_1 \rangle \)，因此 \( S \) 是 \( P \) 中的全序关系。并称它是**字母次序关系**或**字母序**。

例如，\( \langle 2, 2 \rangle S \langle 2, 1 \rangle \)，\( \langle 3, 1 \rangle S \langle 1, 5 \rangle \)
\( \langle 2, 2 \rangle S \langle 2, 2 \rangle \)，\( \langle 3, 2 \rangle S \langle 1, 1 \rangle \)

设$R$是$X$中的全序关系，并设

$P=X\cup X^2\cup\cdots\cup X^n=\bigcup_{i=1}^{n}X^i\quad(n=1,2,\cdots)$

这个方程式说明，$P$是由长度小于或等于$n$的元素串组成的。假定$n$取某个固定值，可把长度为$p$的元素串看成是$P$重序元。这样就可以定义$P$中的全序关系$S$，并称它是字母次序关系。为此，设$\langle x_1,x_2,\cdots,x_p\rangle$和$\langle y_1,y_2,\cdots,y_q\rangle$是集合中的任何两个元素串，且有$p\leq q$。为了满足$P$中的次序关系。首先对两个元素串进行比较。如果需要的话，把两个元素串加以交换，使得$q\leq p$。

如果要使\(\langle x_1, x_2, \cdots, x_p \rangle S \langle y_1, y_2, \cdots, y_q \rangle\)，就必须满足下列条件之一：

- (1) \(\langle x_1, x_2, \cdots, x_p \rangle = \langle y_1, y_2, \cdots, y_p \rangle\)

- (2) \(x_1 \neq y_1\) 且 \(X\) 中有 \(x_1 R y_1\)

- (3) \(x_i = y_i, i = 1, 2, \cdots, k (k < p)\) 且 \(x_{k+1} \neq y_{k+1}\) 和 \(X\) 中有 \(x_{k+1} R y_{k+1}\)

如果上述条件中一个也没有得到满足，则应有
\(\langle y_1, y_2, \cdots, y_q \rangle S \langle x_1, x_2, \cdots, x_p \rangle\)

