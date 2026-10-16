# Solution

we need $P(n) \ge c \cdot 2^{n}$

$P(k) \ge c \cdot 2^{k} \Rightarrow$

$P(n) = \sum_{k=1}^{n-1} P(k)P(n-k)$

$\ge \sum_{k=1}^{n-1} c \cdot 2^{k} \cdot c \cdot 2^{n-k} = \sum_{k=1}^{n-1} c^{2} \cdot 2^{n} = (n-1) \cdot c^{2} \cdot 2^{n}$

$\ge c \cdot 2^{n}$  ( if $(n-1) \cdot c^{2} \ge c$, that is $c \ge \dfrac{1}{n-1}$ )