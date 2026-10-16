# # 残差神经网络（Residual CNN）

![](bbox=[0.031, 0.229, 0.905, 0.999])

$F(x)$

$x$

weight layer

relu

weight layer

$x$

identity

$F(x)+x$

relu

$x^{l+1}=x^l+\mathcal{F}(x^l)$

$x^{l+2}=x^{l+1}+\mathcal{F}(x^{l+1})$

$=x^l+\mathcal{F}(x^l)+\mathcal{F}(x^{l+1})$

$=x^l+\sum_{i=l}^{l+1}\mathcal{F}(x^i)$