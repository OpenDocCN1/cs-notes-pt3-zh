# 支持向量机

# 非线性支持向量机

根据问题和数据不同，选择带有不同的核函数。

一些常用的核函数：

线性核： $k(x_1, x_2) = x_1^T x_2$

多项式核： $k(x_1, x_2) = (<x_1, x_2> + R)^d$

高斯核： $k(x_1, x_2) = \exp\{ -\frac{||x_1 - x_2||^2}{2\sigma^2} \}$

Sigmoid核： $k(x_1, x_2) = \tanh(\beta_0 x_1^T x_2 + \beta_1)$

如何判断一个函数是否可以作为核函数？

Mercer定理：
$\mathbb{R}^n \times \mathbb{R}^n \to \mathbb{R}$ 上的映射 $k$ 是一个有效核函数(也称 Mercer 核函数) 当且仅当 对于训练样本其相应的核函数矩阵是对称半正定的, 即对于任何平方可积函数 $g(x)$ 有 $\iint k(x,y) g(x) g(y) dx dy \ge 0$。