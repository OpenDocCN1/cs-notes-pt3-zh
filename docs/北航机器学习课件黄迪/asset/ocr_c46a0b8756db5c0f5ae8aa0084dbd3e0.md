# # Long Short Term Memory (LSTM)

+   - “遗忘门”

![](bbox=[0.045, 0.305, 0.973, 0.68])

$f_t = \sigma\left(W_f \cdot [h_{t-1}, x_t] + b_f\right)$

# ➢ 选择哪些信息应该被遗忘

先前输出（即隐藏状态）的信息和来自当前输入的信息经sigmoid函数激活，输出介于0~1之间。越接近0意味着越容易被忘记，越接近1则越容易被保留。