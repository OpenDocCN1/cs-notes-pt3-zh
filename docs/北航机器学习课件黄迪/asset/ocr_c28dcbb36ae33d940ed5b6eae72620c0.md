# 线性判别函数齐次化

线性判别函数 $g(x)=w^T x + w_0$

改写成 $g(x)=w_0 + \sum_{i=1}^{d} w_i x_i = \sum_{i=1}^{d} a_i y_i = a^T y$

称为线性判别函数的齐次简化

$y=\begin{bmatrix}1\\x_1\\x_2\\\vdots\\x_d\end{bmatrix}=\begin{bmatrix}1\\x\end{bmatrix}$ 增广样本向量； $a=\begin{bmatrix}w_0\\w_1\\w_2\\\vdots\\w_d\end{bmatrix}=\begin{bmatrix}w_0\\w\end{bmatrix}$ 增广权向量

$\hat d = d + 1$; $y$ 比 $x$ 增加一维，保持样本空间欧式距离不变，变换后的样本仍全部位于 $d$ 维子空间(原 $X$ 空间)中。

方程 $a^T y = 0$ 在 $Y$ 空间确定了一个通过原点的超平面 $\hat H$，它对 $d$ 维子空间的划分与原决策面 $w^T x + w_0 = 0$ 对原 $X$ 空间的划分完全相同。$Y$ 空间中任意一点 $y$ 到 $\hat H$ 的距离： $r = \frac{g(x)}{||a||} = \frac{a^T y}{||a||}$