
## Slice Sampling

- **Metropolis 方法的缺点：**
  - 步长太短：走得太慢（可能随机散步）
  - 步长太长：拒绝率很高，效率较差；

- **SLICE采样可以自适应调整步长**
  - 将 $z$ 空间扩展成 $(z, u)$ 空间

$\hat{p}(z, u) = \begin{cases} 1/Z_p & \text{if } 0 \le u \le \tilde{p}(z) \\ 0 & \text{otherwise} \end{cases}$

$\int \hat{p}(z, u) du = \int_{0}^{\tilde{p}(z)} \frac{1}{Z_p} du = \frac{\tilde{p}(z)}{Z_p} = p(z)$

$\hat{p}(z,u)=\begin{cases}1/Z_p & \text{if }0\le u\le \tilde{p}(z)\\0 & \text{otherwise}\end{cases}\qquad \int \hat{p}(z,u)\,du\int_{0}^{\tilde{p}(z)}\frac{1}{Z_p}\,du=\frac{\tilde{p}(z)}{Z_p}=p(z)$

- **第一步：** 给定 $z$，在 $0\le u\le \tilde{p}(z)$ 范围内均匀分布产生 $u$
- **第二步：** 给定 $u$，在 $\{z:\tilde{p}(z)>u\}$ 范围内均匀分布产生 $z$

![](img/292e77b9b7b40db2ea6f49ac62f8aa0f_867_0.png)

🔴 在实际应用中，很难确定范围

➢ 第一步：给定 $z$，在 $0 \leq u \leq \tilde{p}(z)$ 范围内均匀分布产生 $u$

➢ 第二步：给定 $u$，在 $z_{\min} \leq z \leq z_{\max}$ 范围内均匀分布产生 $z$

![](img/292e77b9b7b40db2ea6f49ac62f8aa0f_868_0.png)

## 机器学习
Machine Learning

北京航空航天大学计算机学院智能识别与图像处理实验室
IRIP Lab, School of Computer Science and Engineering, Beihang University
黄 迪  刘庆杰

2019年秋季学期
Fall 2019

## 课前回顾

## 基本采样法（Basic Sampling）

🔴 **思想：** 从基本概率分布中产生新变量的分布

- 均匀分布（Uniform distribution）：\(p(z)=1,\ z\in(0,1)\)

- 产生非均匀分布：\(p(y),\ y=f(z)\)

\[p(y)=p(z)\left|\frac{dz}{dy}\right|\]

\[p(z)=1\]

\[z=h(y)\equiv\int_{\infty}^{y}p(\hat y)\,d\hat y\]

\[y=h^{-1}(z)\]

## 累积分布函数（CDF）

![](img/292e77b9b7b40db2ea6f49ac62f8aa0f_871_0.png)

## 基本采样法（Basic Sampling）

- 练习：指数分布 $p(y) = \lambda \exp(-\lambda y)\quad y \in [0, \infty)$

求 $y = f(z)$

$h(y) = \int_{-\infty}^{y} p(\hat{y}) d\hat{y} = 1 - \exp(\lambda y)$

$y = h^{-1}(z) = \lambda^{-1} \ln(1 - z)$

- 多变量分布形式：

$p(y_1, ..., y_M) = p(z_1, ..., z_M) \left| \frac{\partial(z_1, ..., z_M)}{\partial(y_1, ..., y_M)} \right|$

## 基本采样法（Basic Sampling）

- **高斯分布：**

$z_1,z_2\sim U(0,1)$

$p(z_1,z_2)=1,\quad (z_1+z_2)^2\le 1$

$y_1=\sqrt{-2\ln z_1}\cos(2\pi z_2)$

$y_2=\sqrt{-2\ln z_1}\sin(2\pi z_2)$

> > 不适用于积分及反函数难求的分布！

$r^2=(z_1+z_2)^2$

$p(y_1,y_2)=p(z_1,z_2)\left|\frac{\partial(z_1,z_2)}{\partial(y_1,y_2)}\right|$

$=\left[\frac{1}{\sqrt{2\pi}}\exp(-y_1^2/2)\right]\left[\frac{1}{\sqrt{2\pi}}\exp(-y_2^2/2)\right]$

**Box-Muller变换**

## 拒绝采样（Rejection Sampling）

- 对一个很复杂的分布 $p(z)$ 进行采样，不能给出其具体的解析形式，但是每个 $z$ 可以估算其比例

$$p(z)=\frac{1}{Z}p'(z)$$

其中 $Z$ 未知，$p'(z)$ 已知。

- 用 $q(z)$ 去逼近 $\tilde{p}(z)$

$$kq(z)\geq \tilde{p}(z)$$

![](img/292e77b9b7b40db2ea6f49ac62f8aa0f_874_0.png)

$q(z)$ 称为建议分布 proposal distribution

## 拒绝采样（Rejection Sampling）

🔴 采样步骤

1、从 $q(z)$ 中产生 $z_0$
2、从 $[0, kq(z_0)]$ 均匀分布中产生 $\mu_0$
3、如果 $\mu_0 > \tilde{p}(z_0)$ 拒绝采样，否则接受采样

![](img/292e77b9b7b40db2ea6f49ac62f8aa0f_875_0.png)

$$p(\mathrm{accept}) = \int \{\tilde{p}(z)/kq(z)\}q(z)\,dz = \frac{1}{k}\int \tilde{p}(z)\,dz$$

拒绝采样又称为接受-拒绝采样（Acceptance-Rejection Sampling）

## 重要性采样（Importance Sampling）

- 对于个变量 $z \sim p(z)$，一个关于 $z$ 函数 $f(z)$，预测 $f(z)$ 的期望值：

$$\mathbb{E}(f)=\int f(z)p(z)\,dz$$

- $p(z)$ 很复杂，或者无法写出解析形式，但可以估算每个出现在 $z$ 的概率 $p(z)$。要估计

$$\mathbb{E}(f)=\int f(z)p(z)\,dz$$

- 可以按如下方式计算-将空间网络化

$$\mathbb{E}(f)\approx\sum_{l=1}^{L}p\left(z^{(l)}\right)f\left(z^{(l)}\right)$$

$$\mathbb{E}(f) \approx \sum_{l=1}^{L} p(z^{(l)})f(z^{(l)})$$

- **直接计算** $\mathbb{E}(f)$ 有两个困难：
  - 维数灾难
  - 效率低下

![](img/292e77b9b7b40db2ea6f49ac62f8aa0f_878_0.png)

## 重要性采样（Importance Sampling）

- 与拒绝采样类似，借助一个容易采样的建议分布 $q(z)$

$$\mathbb{E}(f)=\int f(z)p(z)\,dz$$

$$=\int f(z)\frac{p(z)}{q(z)}q(z)\,dz$$

$$\approx \frac{1}{L}\sum_{l=1}^{L}\frac{p(z^{(l)})}{q(z^{(l)})}f(z^{(l)})$$

![](img/292e77b9b7b40db2ea6f49ac62f8aa0f_879_0.png)

## 重要性采样 (Importance Sampling)

- 考虑更一般的形式，即 $p(z) = \frac{1}{Z_p}\tilde p(z)$，此时 $\tilde p(z)$ 同样地，$q(z)$也具有类似的性质，即 $q(z) = \frac{1}{Z_q}\tilde q(z)$

- 此时：
$\mathbb{E}(f) = \int f(z)p(z)dz$
$= \frac{Z_q}{Z_p}\int f(z)\frac{\tilde p(z)}{\tilde q(z)}q(z)dz$
$\approx \frac{Z_q}{Z_p}\frac{1}{L}\sum_{l=1}^{L}\tilde r_l f(z^{(l)})$

其中 $\tilde r_l = \frac{\tilde p(z^{(l)})}{\tilde q(z^{(l)})}$ 重要性权重
