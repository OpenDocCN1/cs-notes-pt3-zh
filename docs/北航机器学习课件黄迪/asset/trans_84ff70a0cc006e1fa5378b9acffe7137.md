

## 第九讲：人工神经网络（续）

第九章：人工神经网络

### 常见激活函数

- Swish函数

$$\operatorname{swish}(x)=x\sigma(\beta x)$$

![](img/292e77b9b7b40db2ea6f49ac62f8aa0f_644_0.png)

- 常见激活函数及其导数

| 激活函数 | 函数 | 导数 |
| --- | --- | --- |
| Logistic 函数 | $f(x) = \frac{1}{1+\exp(-x)}$ | $f'(x) = f(x)(1 - f(x))$ |
| Tanh 函数 | $f(x) = \frac{\exp(x)-\exp(-x)}{\exp(x)+\exp(-x)}$ | $f'(x) = 1 - f(x)^2$ |
| ReLU | $f(x) = \max(0, x)$ | $f'(x) = I(x > 0)$ |
| ELU | $f(x) = \max(0, x) + \min(0, \gamma(\exp(x) - 1))$ | $f'(x) = I(x > 0) + I(x \le 0) \cdot \gamma \exp(x)$ |
| SoftPlus 函数 | $f(x) = \log(1 + \exp(x))$ | $f'(x) = \frac{1}{1+\exp(-x)}$ |

### 感知器

![](img/292e77b9b7b40db2ea6f49ac62f8aa0f_646_0.png)

输入层神经元

输出层神经元

$$y=f(a)=f\left(\sum_{i=1}^{N}w_i x_i\right)$$

![](img/292e77b9b7b40db2ea6f49ac62f8aa0f_646_1.png)

输入层神经元

输出层神经元

$$y_j=f(a_j)=f\left(\sum_{i=1}^{N}w_{ij}x_i\right)$$

### 多层感知器

- 对于异或问题，用一个简单的三层感知器就可得到解决。

![](img/292e77b9b7b40db2ea6f49ac62f8aa0f_647_0.png)

| $x_1$ | $x_2$ | $y$ |
| --- | --- | --- |
| 0 | 0 | 0 |
| 0 | 1 | 1 |
| 1 | 0 | 1 |
| 1 | 1 | 0 |

理论证明，三层感知器可以实现任意的逻辑运算，在激活函数为 Sigmoid 函数的情况下，可以逼近任何非线性多元函数。

### 如何训练神经网络？

- 定义准则函数

$$E(\mathbf{w}) = \frac{1}{2} \sum_{n=1}^{N} \left\{ y(\mathbf{x}_n, \mathbf{w}) - t_n \right\}^2$$

寻找一个 $\mathbf{w}$，使得 $E(\mathbf{w})$ 最小。

$$\nabla E(\mathbf{w}) = 0$$

$$\mathbf{w}^{(\tau+1)} = \mathbf{w}^{(\tau)} - \eta \nabla E(\mathbf{w}^{(\tau)})$$

### BP反向传播算法

- 样本集 $\{\mathbf{x}_n,t_n\}_{n=1}^{N},\ \mathbf{x}\in\mathbb{R}^{D},\ \mathbf{t}\in\mathbb{R}^{3}$

![](img/292e77b9b7b40db2ea6f49ac62f8aa0f_650_0.png)

$$y_k=\sum_{i=1}^{D}w_{ki}x_i$$

$$E_n(\mathbf{w})=\frac{1}{2}\sum_{k=1}^{3}(y_{nk}-t_{nk})^2$$

![](img/292e77b9b7b40db2ea6f49ac62f8aa0f_650_1.png)

$$\frac{\partial E_n}{\partial w_{ki}}=(y_{nk}-t_{nk})x_{ni}$$

练习：对非线性 $y_k = h(a_k) = h\left(\sum_i w_{ki}x_i\right)$

计算 $\frac{\partial E_n}{\partial w_{ki}}$，其中 $E_n = \frac{1}{2}\sum_k (y_k - t_k)^2$。

$$
\frac{\partial E_n}{\partial w_{ki}} = \frac{\partial E_n}{\partial y_k}\frac{\partial y_k}{\partial a_k}\frac{\partial a_k}{\partial w_{ki}}
$$

$$
= (y_k - t_k)\frac{\partial y_k}{\partial a_k}\frac{\partial a_k}{\partial w_{ki}}
$$

$$
= (y_k - t_k)h'(a_k)\frac{\partial a_k}{\partial w_{ki}}
$$

$$
= (y_k - t_k)h'(a_k)x_i
$$

![](img/292e77b9b7b40db2ea6f49ac62f8aa0f_652_0.png)

$$
a_j = \sum_i w_{ji} z_i, \quad z_j = h(a_j)
$$

$$
\frac{\partial E_n}{\partial w_{ji}} = \frac{\partial E_n}{\partial a_j} \cdot \frac{\partial a_j}{\partial w_{ji}}
$$

$$
\delta_j \equiv \frac{\partial E_n}{\partial a_j}
$$

$$
\frac{\partial a_j}{\partial w_{ji}} = z_i
$$

$$
\frac{\partial E_n}{\partial w_{ji}} = \delta_j z_i
$$

对于输出层而言：

$$
\delta_k = y_k - t_k
$$

对于隐藏层而言：

$$
\delta_j \equiv \frac{\partial E_n}{\partial a_j} = \sum_{k} \frac{\partial E_n}{\partial a_k} \frac{\partial a_k}{\partial a_j}
$$

$$
\delta_j = h'(a_j) \sum_{k} w_{kj} \delta_k
$$

![](img/292e77b9b7b40db2ea6f49ac62f8aa0f_653_0.png)

- 练习：$a_k = \sum_j w_{kj}z_j, \quad z_j = h(a_j)$

推导

$$
\delta_j = h'(a_j)\sum_k w_{kj}\delta_k
$$

$$
\delta_j = \sum_k \frac{\partial E_n}{\partial a_k}\frac{\partial a_k}{\partial a_j} = \sum_k \delta_k\frac{\partial a_k}{\partial a_j}
$$

![](img/292e77b9b7b40db2ea6f49ac62f8aa0f_654_0.png)

$$
= \sum_k \delta_k\frac{\partial a_k}{\partial z_j}\frac{\partial z_j}{\partial a_j} = \sum_k \delta_k w_{kj}\frac{\partial h(a_j)}{\partial a_j}
$$

$$
= h'(a_j)\sum_k \delta_k w_{kj}
$$

- 初始化权重 $w_{ij}$
- 对于输入的训练样本，求取每个节点输出和最终输出层的输出值
- 对输出层求取 $\delta_k = y_k - t_k$
- 对于隐藏层求取 $\delta_j = h'(a_j)\sum_k w_{kj}\delta_k$
- 求取输出误差对于每个权重的梯度 $\frac{\partial E_n}{\partial w_{ji}} = \delta_j z_i$
- 更新权重 $\mathbf{w}^{(\tau+1)} = \mathbf{w}^{(\tau)} - \eta \nabla E(\mathbf{w}^{(\tau)})$

- 多层前馈网络的学习算法比较复杂，其主要困难是中间的隐层不直接与外界连接，无法直接计算其误差。
- 反向逐层传播输出层的误差，以间接算出隐层误差。算法分为两个阶段：
  - **第一阶段(正向传播过程)** 输入信息从输入层经隐层逐层计算各单元的输出值；
  - **第二阶段(反向传播过程)** 由输出误差逐层向前算出隐层各单元的误差，并用此误差修正前层权值。

