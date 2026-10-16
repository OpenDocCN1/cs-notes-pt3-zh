# 残差神经网络（Residual CNN）

![](bbox=[0.04, 0.27, 0.3, 0.96])

损失函数: $E$    求 $\frac{\partial E}{\partial x^l}$

$\frac{\partial E}{\partial x^l} = \frac{\partial E}{\partial x^L} \frac{\partial x^L}{\partial x^l}$

$= \frac{\partial E}{\partial x^L} \left( 1 + \frac{\partial \sum_{i=l}^{L-1} \mathcal{F}(x^i)}{\partial x^l} \right)$