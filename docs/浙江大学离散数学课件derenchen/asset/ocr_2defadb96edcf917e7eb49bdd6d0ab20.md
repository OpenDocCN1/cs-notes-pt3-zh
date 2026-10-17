证：(2) 对任意集合 $A$，都有 $A^* = P(A)$。

我们来证明任何函数 $g:A\to P(A)$ 都不是满射。

设 $g:A\to P(A)$ 是从 $A$ 到 $P(A)$ 的函数。如果对 $\forall x\in A$，都有 $x\in g(x)$，则 $\varnothing\in P(A)$ 在 $g$ 下无原像，从而 $g$ 不是满射。

下面假设 $\exists x\in A$，使 $x\notin g(x)$，此时，集合

$B=\{x\mid x\in A\land x\notin g(x)\}$

非空，且 $B\in P(A)$。但对 $\forall x\in A$，都有 $x\in B\Leftrightarrow x\notin g(x)$。

由此可见，对 $\forall x\in A$，都有 $g(x)\ne B$。从而 $B$ 在 $g$ 下无原像。