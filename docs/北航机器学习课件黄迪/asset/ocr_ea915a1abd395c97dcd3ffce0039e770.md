# 最小二乘准则

寻找最好投影方向 $a^*$

$a^T y_n > 0$

$a^T y_n = b_n > 0$    $b_n$是任意给定的正常数

方程组形式：

$Y a = b$

$Y = \begin{bmatrix} y_1^T \\ y_2^T \\ \vdots \\ y_N^T \end{bmatrix} = \begin{bmatrix} y_{11} & y_{12} & \cdots & y_{1\hat{d}} \\ y_{21} & y_{22} & \cdots & y_{2\hat{d}} \\ \cdots & \cdots & \cdots & \cdots \\ y_{N1} & y_{N2} & \cdots & y_{N\hat{d}} \end{bmatrix}$

$y_n$是规范化增广向量样本
$Y$是$N \times \hat{d}$维矩阵，通常$N > \hat{d}$，一般为列满秩阵

$b = [b_1 \quad b_2 \quad \cdots \quad b_N]$

$b$是$N$维向量，$b_n > 0$， $n=1,2,...,N$

方程数多于未知数的矛盾方程组通常没有精确解

定义误差向量：$e = Y a - b$及平方误差准则函数

$J_S(a) = \|e\|^2 = \|Y a - b\|^2 = \sum_{n=1}^{N} (a^T y_n - b_n)^2$