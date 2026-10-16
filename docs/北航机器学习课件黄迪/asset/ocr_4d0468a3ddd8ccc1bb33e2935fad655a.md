# 逻辑回归(Logistic Regression)

# 将回归问题转为分类问题

逻辑回归是概率型非线性回归，但其本质是线性回归，只是在特征到结果的映射中加入了一层函数映射，即先把特征线性求和，然后使用函数 σ(z) 来预测。

多类问题：

p(C_k|x) = p(x|C_k)p(c_k) / Σ_j p(x|C_j)p(c_j) = exp(a_k) / Σ_j exp(a_j)
a_k = ln p(x|C_k)p(c_k)

归一化指数
Normalized Exponential

Softmax函数

是一个平滑的max函数，对于所有的 k ≠ j，如果 a_k ≫ a_j，有 p(C_k|x) ≈ 1
p(C_j|x) ≈ 0