# $B=AA^T$ 在图上的意义

定义矩阵 $B=AA^T$。设 $a_{ij}$ 是邻接矩阵中的第 $i$ 行和第 $j$ 列上的 $(i,j)$ 元素，$b_{ij}$ 是矩阵中的第 $i$ 行和第 $j$ 列上的元素 $(i,j)$。于是，对于 $i,j=1,2,3,\cdots,n$ 来说，有

$$b_{ij}=\sum_{k=1}^{n}a_{ik}a_{jk}$$

如果边 $\langle v_i,v_k\rangle\in E$，则有 $a_{ik}=1$；如果边 $\langle v_j,v_k\rangle\in E$，则有 $a_{jk}=1$。对于某一个确定的 $k$ 来说，如果 $\langle v_i,v_k\rangle$ 和 $\langle v_j,v_k\rangle$ 都是给定图的边，则在表示 $b_{ij}$ 的上述求和和表达式中，应该引入基值 1。从结点 $v_i$ 和 $v_j$ 二者引出的边，如果能共同终止于一些结点的话，那么这样的一些结点的数目，就是元素 $b_{ij}$ 的值。