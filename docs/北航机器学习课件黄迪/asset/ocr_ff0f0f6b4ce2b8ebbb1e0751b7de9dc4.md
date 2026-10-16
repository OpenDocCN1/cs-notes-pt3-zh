# 感知机准则

+   🔴 求使 $J_P(a)$ 达到最小值 $a^*$

采用梯度下降法求解 $J_P(a)=\sum_{y\in\eta^k}(-a^T y)$

$\nabla J_P(a)=\frac{\partial J_P(a)}{\partial a}=\sum_{y\in\eta^k}(-y)$

$a(k+1)=a(k)-\rho_k\nabla J$

梯度下降法迭代公式

$a(k+1)=a(k)+\rho_k\nabla\sum_{y\in\eta^k}y$

![](bbox=[0.181, 0.741, 0.827, 0.972])