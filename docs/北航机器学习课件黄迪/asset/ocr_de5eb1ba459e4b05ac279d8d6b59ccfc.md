# # K均值算法

+   - 对于样本 $\mathbf{x}_n$，定义一个聚类标注 $r_n$，即如果 $\mathbf{x}_n$ 属于第 $k$ 个聚类，那么 $r_{nk}=1$，否则 $r_{nk}=0$。

+   - 准则函数：

$J=\sum_{n=1}^{N}\sum_{k=1}^{K}r_{nk}\lVert\mathbf{x}_n-\boldsymbol{\mu}_k\rVert^2$

![](bbox=[0.078, 0.66, 0.924, 0.984])