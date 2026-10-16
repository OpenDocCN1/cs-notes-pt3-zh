# # 反向传播(BP)算法

![](bbox=[0.039, 0.295, 0.426, 0.671])

$y_k = \sum_i w_{ki}x_i$

$E_n = \frac{1}{2}\sum_k (y_{nk}-t_{nk})^2$

$E(\mathbf{w}) = \sum_{n=1}^{N} E_n(\mathbf{w})$

$\frac{\partial E_n}{\partial w_{jk}} = (y_{nk}-t_{nk})x_{nk}$

误差