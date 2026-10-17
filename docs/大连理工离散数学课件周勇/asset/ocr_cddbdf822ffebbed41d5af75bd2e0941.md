# # 等幂函数

定义：给定函数\(f: X \to X\)，如果有\(f^2 = f\)，则称\(f\)是个等幂函数。

例：设\(I\)是整数集合和\(N_m = \{0, 1, 2, \cdots m-1\}\)，并且函数\(f: I \to N_m\)是\(f(i) = i(\text{mod } m)\)。试证明，对于\(n \geqslant 1\)都有\(f^n = f\)。

证明： （归纳证法）当\(n=2\)时

\(f^2 = f \circ f = f(f(i)) = f(i(\text{mod } m))\)

\(= (i(\text{mod } m))(\text{mod } m) = i(\text{mod } m) = f\)

假设当\(n=k\)时，满足\(f^k = f\)；

那么当\(n=k+1\)时，

\(f^{k+1} = f^k \circ f = f \circ f = f\)

得证。对于所有的\(n \geqslant 1\)，都有\(f^n = f\)