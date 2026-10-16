# # 0-1背包问题

设所给0-1背包问题的子问题

\(max\sum_{k=i}^nv_kx_k\left\{\begin{array}{ c }
\sum_{k=i}^nw_kx_k\le j \\
x_k\in\{0,1\},i\le k\le n
\end{array}\right.\)

的最优值为m(i, j)，即m(i, j)是背包容量为j，可选择物品为i，i+1，...，n时0-1背包问题的最优值。由0-1背包问题的最优子结构性质，可以建立计算m(i, j)的递归式如下。

\(m(i,j)=\left\{\begin{array}{ c }
max\{m(i+1,j),m(i+1,j-w_i)+v_i\} \\
m(i+1,j)
\end{array}\right.\)

\(m(n,j)=\left\{\begin{array}{ c }
v_n \\
0
\end{array}\right.\)