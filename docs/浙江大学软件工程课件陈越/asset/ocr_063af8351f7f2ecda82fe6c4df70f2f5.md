# 第2步：计算CFG的环形复杂度
(Cyclomatic Complexity)

已知公式：\( V(G) = m - n + p \)

其中\( V(G) \)为强连通有向图G中线性无关环
(independent paths)的个数(称为 cyclomatic
number of G)；\( m \)是边数 (number of edges)；\( n \)
是 节 点 数(number of nodes)；\( p \) 是G中连通
集的数目(number of connected components)。