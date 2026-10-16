# # 主成分分析-算法

# 🔴 最小均方误差思想

使原数据与降维后的数据（在原空间中的重建）的误差最小

那么 $\mathbf{x}_n = \sum_{i=1}^{D}(\mathbf{x}_n^T\mathbf{u}_i)\mathbf{u}_i$

在 $M$ 维变量（$M<D$）生成的空间中对其进行表示

$\tilde{\mathbf{x}}_n = \sum_{i=1}^{M} z_{ni}\mathbf{u}_i + \sum_{i=M+1}^{D} b_i\mathbf{u}_i$

独特的　　　　　　　　　　共享的

目标最小化失真度　$J=\frac{1}{N}\sum_{n=1}^{N}\|\mathbf{x}_n-\tilde{\mathbf{x}}_n\|^2$

导数置零得到　$z_{nj}=\mathbf{x}_n^T\mathbf{u}_j,\ j=1,\ldots,M$

$b_j=\bar{\mathbf{x}}^T\mathbf{u}_j,\ j=M+1,\ldots,D$