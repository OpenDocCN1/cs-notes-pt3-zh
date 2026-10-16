# 残差神经网络（Residual CNN）

![](bbox=[0.03, 0.22, 0.92, 0.95])

F(x)
F(x) + x
x^{l+1} = x^{l} + F(x^{l})
x^{l+2} = x^{l+1} + F(x^{l+1})
= x^{l} + F(x^{l}) + F(x^{l+1})
= x^{l} + Σ_{i=l}^{l+1} F(x^{i})