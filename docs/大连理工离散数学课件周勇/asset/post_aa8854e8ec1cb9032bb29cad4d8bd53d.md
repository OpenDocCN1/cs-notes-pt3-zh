
## 函数的基本概念和性质

例：设 \( N \) 是自然数集合，函数 \( S: N \to N \) 定义成  \( S(n) = n+1 \)。显然，\( S(0)=1, S(1)=2, S(2)=3 \cdots \)。这样的函数，通常称为**皮亚诺后继函数**。

注意：有时为了某种需要，要特别强调函数的任意性和唯一性性质：函数 \( f \) 的定义域 \( \operatorname{dom} f \) 中的每一个 \( x \)，在值域 \( \operatorname{ran} f \) 中都恰有一个象点 \( y \)，这种性质通常被称为函数的**良定性**。

## 函数的相等

定义： 给定函数\(f: X \to Y\)和\(g: Z \to W\)。如果\(f\)和\(g\)具有同样的定义域和陪域，亦即\(X=Z\)和\(Y=W\)，并且对于所有的\(x \in X\)或\(x \in Z\)都有\(f(x)=g(x)\)，则称函数\(f\)和\(g\)是相等的，记作\(f=g\)。

求证明函数相等的方法？

## 函数的扩大和缩小

定义：给定函数\(f: X \to Y\)，且有\(A \subseteq X\)。

- （1）试构成一个从\(A\)到\(Y\)的函数 \(g = f \cap (A \times Y)\)。通常称\(g\)是函数\(f\)的**缩小**，并记作\(f|A\)。
- （2）如果\(g\)是\(f\)的缩小，则称\(f\)是\(g\)的**扩大**。

从定义可以看出，函数\(f|A: A \to Y\)的域是集合\(A\)，而函数\(f\)的域则是集合\(X\)。\(f|A\)和\(f\)的陪域均是集合\(Y\)。于是若\(g\)是\(f\)的缩小，则应有

\(\operatorname{dom} g \subseteq \operatorname{dom} f \text{ 且 } g \subseteq f\)

并且对于任何\(x \in \operatorname{dom} g\)都有\(g(x) = (f|A)(x) = f(x)\)。

例：设 $X_1=\{0,1\},X_2=\{0,1,2\},Y=\{a,b,c,d\}$。定义从 $X_1^2$ 到 $Y$ 的函数为：

$f=\{\langle \langle 0,0\rangle,a\rangle,\langle \langle 0,1\rangle,b\rangle,\langle \langle 1,0\rangle,c\rangle,\langle \langle 1,1\rangle,b\rangle\}$。

$g=f\cup\{\langle \langle 0,2\rangle,a\rangle,\langle \langle 2,2\rangle,d\rangle\}$ 是从 $X_1^2\cup\{\langle 0,2\rangle,\langle 2,2\rangle\}$ 到 $Y$ 的函数。

于是 $f=g|X_1^2$，因此 $f$ 是 $g$ 在 $X_1^2$ 上的缩小（或称限制），$g$ 是 $f$ 到 $X_1^2\cup\{\langle 0,2\rangle,\langle 2,2\rangle\}$ 上的扩大（或称延拓）。

## 函数的表示

因为函数是二元关系，所以可以用关系图和关系矩阵来表达函数。

![](img/d475a943ed426379b80e793b9fe1f17d_498_0.png)

函数 \(f: X \to Y\) 的图解

例： 设集合\(X=\{a,b,c,d\}\)和\(Y=\{1,2,3,4,5\}\)，并且有  
\(f=\{\langle a,1\rangle,\langle b,3\rangle,\langle c,4\rangle,\langle d,4\rangle\}\)

试求出\(\operatorname{dom} f\)，\(\operatorname{ran} f\)和\(f\)的矩阵表达式。

解： \(\operatorname{dom} f=\{a,b,c,d\}\)

\(\operatorname{ran} f=\{1,3,4\}\)

\(M_f =\)

|   | 1 | 2 | 3 | 4 | 5 |
|---|---|---|---|---|---|
| a | 1 | 0 | 0 | 0 | 0 |
| b | 0 | 0 | 1 | 0 | 0 |
| c | 0 | 0 | 0 | 1 | 0 |
| d | 0 | 0 | 0 | 1 | 0 |

= \(\begin{bmatrix} 1 & 0 & 0 & 0 & 0 \\ 0 & 0 & 1 & 0 & 0 \\ 0 & 0 & 0 & 1 & 0 \\ 0 & 0 & 0 & 1 & 0 \end{bmatrix}\)

由函数的定义可知，在关系矩阵的每一个行上，都有且仅有一个元素的值是1，而此行上的其他元素都必定为0。因此，可以用一个单独的列来代替关系矩阵。在这个单独的列上，应标明所对应的给定函数的各个值。这样，该列上的各元素也说明了自变量与其函数值之间的对应关系。

上例中\(f\)的简化关系矩阵为：

\(M_f =\)

|   |   |
|---|---|
| a | 1 |
| b | 3 |
| c | 4 |
| d | 4 |

## 函数的构成

设 $A$ 和 $B$ 都是有限集合，且 $|A|=m$ 和 $|B|=n$，因为任何函数 $f:A\to B$ 的定义域都是集合 $A$，所以每个函数中都恰有 $m$ 个序偶。而且，任何元素 $x\in A$，都可以在 $B$ 的 $n$ 个元素中任选其一作为自己的象点。因此，应有 $n^m$ 个可能的不同函数，亦即

$|B^A|=|B|^{|A|}=n^m$

例：设 $A$ 为任意集合，$B$ 为任意非空集合。

- （1）因为存在唯一的一个从 $\varnothing$ 到 $A$ 的函数，所以 $A^\varnothing=\{\varnothing\}$。
- （2）因为不存在从 $B$ 到 $\varnothing$ 的函数，所以 $\varnothing^B=\varnothing$。

## 5.2 函数的合成和合成函数的性质

定义：设\(f: X \rightarrow Y\)和\(g: Y \rightarrow Z\)是两个函数。于是，合成关系\(f \circ g\)为\(f\)与\(g\)的合成函数，并用\(g \circ f\)表示。即  
\(g \circ f = \{(x, z) \mid (x \in X) \wedge (z \in Z) \wedge (\exists y)(y \in Y \wedge y = f(x) \wedge z = g(y))\}\)

注意：合成函数\(g \circ f\)与合成关系\(f \circ g\)实际上表示同一个集合。这种表示方法的不同有其方便之处：

对合成函数\(g \circ f\)，当\(z = (g \circ f)(x)\)时，必有\(z = g(f(x))\)  
\(g \circ f\)与\(g(f(x))\)的次序是理想的。

函数f的值域是函数g的定义域Y的子集，亦即\(\operatorname{ran} f \subseteq \operatorname{dom} g\)。条件\(\operatorname{ran} f \subseteq \operatorname{dom} g\)能确保合成函数\(g\circ f\)是非空的。否则，合成函数\(g\circ f\)是空集。如果\(g\circ f\)非空，则能保证\(g\circ f\)是从X到Z的函数。

定理：设\(f:X\to Y\)和\(g:Y\to Z\)是两个函数：

- （1）合成函数\(g\circ f\)是从\(X\to Z\)的函数，并且对于每一个\(x\in X\)，都有\((g\circ f)(x)=g(f(x))\)。
- （2）\(\operatorname{dom}(g\circ f)=f^{-1}[\operatorname{dom}g],\ \operatorname{ran}(g\circ f)=g[\operatorname{ran}f]\)。

其中\(f^{-1}[\operatorname{dom}g]\)表示g的定义域在f下的原象集，\(g[\operatorname{ran}f]\)表示f的值域在g下的象点集。

证明：(1)假设\(x \in X\)和\(z_1, z_2 \in Z\)，再假设\(\langle x, z_1 \rangle \in g \circ f\)和\(\langle x, z_2 \rangle \in g \circ f\)。这个假设要求存在\(y \in Y\)，能使\(y=f(x)\)，\(z_1=g(y)\)以及\(z_2=g(y)\)。因为\(g\)是一个函数，所以由函数值的唯一性可知，除非\(z_1=z_2\)，否则不可能有\(z_1=g(y)\)和\(z_2=g(y)\)。也就是说，仅能有\(z_1=z_2=z\)和\(\langle x, z \rangle \in g \circ f\)。因此\(g \circ f\)是一个从\(X\)到\(Z\)的函数，且

\((g \circ f)(x) = z = g(y) = g(f(x))\)

(2)若 \( x \in \operatorname{dom}(g \circ f) \)，则存在 \( z \in Z \) 使 \( \langle x,z \rangle \in g \circ f \)。因此，必有 \( y \in Y \) 使 \( \langle x,y \rangle \in f \) 且 \( \langle y,z \rangle \in g \)。但由 \( \langle y,z \rangle \in g \) 知 \( y \in \operatorname{dom} g \)，再由 \( \langle x,y \rangle \in f \)，即得 \( x \in f^{-1}[\operatorname{dom} g] \)。

另一方面，若 \( x \in f^{-1}[\operatorname{dom} g] \)，则有 \( y \in \operatorname{dom} g \) 使 \( \langle x,y \rangle \in f \)。但由 \( y \in \operatorname{dom} g \) 知，有 \( z \in Z \) 使 \( \langle y,z \rangle \in g \)，所以 \( \langle x,z \rangle \in g \circ f \)，这表明 \( x \in \operatorname{dom}(g \circ f) \)。

同理可证 \( \operatorname{ran}(g \circ f) = g[\operatorname{ran} f] \)。
