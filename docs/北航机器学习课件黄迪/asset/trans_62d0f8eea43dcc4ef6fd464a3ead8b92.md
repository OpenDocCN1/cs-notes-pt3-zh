

## 批处理梯度下降
(Batch Gradient Descent)

在梯度下降方法中，每次更新都利用所有数据，即：

```
w_j^t = w_j^{t-1} - α Σ_{i=1}^N (f(x_i) - y_i) · x_j
```

在大样本条件下，批处理梯度下降的迭代速度很慢

![](img/292e77b9b7b40db2ea6f49ac62f8aa0f_129_0.png)

![](img/292e77b9b7b40db2ea6f49ac62f8aa0f_129_1.png)

## 随机梯度下降
(Stochastic Gradient Descent)

基本思想：如果条件对所有样本都成立，则对任一样本也成立
每次只用一个样本 (x_r, y_r)
$w_j^t = w_j^{t-1} - \alpha (f(x_r) - y_r) \cdot x_{r,j}$

- 收敛速度较快
- 不太容易陷入局部极值
- 对大样本数据较有效

又称在线学习(Online Learning)

变化形式

可离线学习，每次“看”一个样本，对所有样本循环使用多次(一次循环称为一个Epoch)
每次可以看一些样本(Mini-Batch)

## $f_w(x)$
(for fixed $w_0, w_1$, this is a function of $x$)

![](img/292e77b9b7b40db2ea6f49ac62f8aa0f_131_0.png)

## $J(w)$
(function of the parameters $w_0, w_1$)

![](img/292e77b9b7b40db2ea6f49ac62f8aa0f_131_1.png)

## f_w(x)
(for fixed w0, w1, this is a function of x)

## J(w)
(function of the parameters w0, w1)

![](img/292e77b9b7b40db2ea6f49ac62f8aa0f_132_0.png)

![](img/292e77b9b7b40db2ea6f49ac62f8aa0f_132_1.png)

## $f_w(x)$
(for fixed $w_0, w_1$, this is a function of $x$)

## $J(w)$
(function of the parameters $w_0, w_1$)

![](img/292e77b9b7b40db2ea6f49ac62f8aa0f_133_0.png)

![](img/292e77b9b7b40db2ea6f49ac62f8aa0f_133_1.png)

## $f_w(x)$
(for fixed $w_0, w_1$, this is a function of $x$)

![](img/292e77b9b7b40db2ea6f49ac62f8aa0f_134_0.png)

## $J(w)$
(function of the parameters $w_0, w_1$)

![](img/292e77b9b7b40db2ea6f49ac62f8aa0f_134_1.png)

## $f_w(x)$
(for fixed $w_0, w_1$, this is a function of x)

## $J(w)$
(function of the parameters $w_0, w_1$)

![](img/292e77b9b7b40db2ea6f49ac62f8aa0f_135_0.png)

![](img/292e77b9b7b40db2ea6f49ac62f8aa0f_135_1.png)

## f_w(x)
(for fixed w0, w1, this is a function of x)

## J(w)
(function of the parameters w0, w1)

![](img/292e77b9b7b40db2ea6f49ac62f8aa0f_136_0.png)
Price $ (in 1000s)

Size (feet²)

Training data

Current hypothesis

![](img/292e77b9b7b40db2ea6f49ac62f8aa0f_136_1.png)

## f_w(x)
(for fixed w0, w1, this is a function of x)

![](img/292e77b9b7b40db2ea6f49ac62f8aa0f_137_0.png)

## J(w)
(function of the parameters w0, w1)

![](img/292e77b9b7b40db2ea6f49ac62f8aa0f_137_1.png)

## f_w(x)
(for fixed w0, w1, this is a function of x)

## J(w)
(function of the parameters w0, w1)

![](img/292e77b9b7b40db2ea6f49ac62f8aa0f_138_0.png)

![](img/292e77b9b7b40db2ea6f49ac62f8aa0f_138_1.png)

## f_w(x)
(for fixed w0, w1, this is a function of x)

## J(w)
(function of the parameters w0, w1)

Price $ (in 1000s)

Size (feet²)

Training data

Current hypothesis

![](img/292e77b9b7b40db2ea6f49ac62f8aa0f_139_0.png)

![](img/292e77b9b7b40db2ea6f49ac62f8aa0f_139_1.png)

## 标准方程组
(Normal Equations)

- 目标函数：
  $J(\mathbf{w}) = \sum_{i=1}^{N} (f(\mathbf{x}_i) - y_i)^2$
  $= \sum_{i=1}^{N} (\mathbf{w}^T \mathbf{x}_i - y_i)^2$

- 直接求导，并令其等于0，求得极值

## 标准方程组
(Normal Equations)

- 将目标函数写成矩阵形式：

J(w) = Σ_{i=1}^{N} (w^T x_i - y_i)^2
= (X w - y)^T (X w - y)

- 其中

X = (x_1^T \ x_2^T \ ... \ x_N^T) = (x_{11}, x_{12}, ..., x_{1m} \ x_{21}, x_{22}, ..., x_{2m} \ ... \ x_{N1}, x_{N2}, ..., x_{Nm})

y = (y_1 \ y_2 \ ... \ y_N)^T

## 标准方程组
(Normal Equations)

- 求导：
  ∂J(w)/∂w = ∂/∂w (Xw - y)^T (Xw - y)
  = 2 X^T (Xw - y) = 0
  ⇒ X^T X w = X^T y

- 得到模型的参数：
  ŵ = (X^T X)^{-1} X^T y

## 梯度下降 vs 标准方程组

- 🔴 **梯度下降法：**
  - 需要选择 α
  - 需要迭代多次
  - 需要数据归一化
  - 样本量非常大时也适用

- 🔴 **标准方程组：**
  - 不需要选择 α
  - 不需要迭代多次
  - 无需数据归一化
  - 样本量大时不适用
    （需要计算 $(X^T X)^{-1}$）

样本量较小时选用标准方程组求解
样本量较大时选用梯度下降法求解

## 再看曲线拟合

![](img/292e77b9b7b40db2ea6f49ac62f8aa0f_144_0.png)

## 最大似然估计

p(t|x, w, β) = ∏_{n=1}^N N(t_n | y(x_n, w), β^{-1})

ln p(t|x, w, β) = - β/2 ∑_{n=1}^N {y(x_n, w) - t_n}^2 + N/2 ln β - N/2 ln(2π)

Determine w_ML by minimizing sum-of-squares error, E(w).

p(t|x, w_ML, β_ML) = N(t | y(x, w_ML), β_ML^{-1})

