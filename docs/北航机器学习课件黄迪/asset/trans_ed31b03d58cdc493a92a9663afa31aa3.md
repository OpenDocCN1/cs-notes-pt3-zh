

## 感知机准则-示例

### 示例（续）

**迭代过程**

**(7)**

\[
\mathbf{y}^{(7)\top}=(-1\quad -2\quad -1)
\]

\[
\mathbf{a}(7)^\top\mathbf{y}^{(7)}=(2\quad -2\quad 1)\begin{pmatrix}-1\\-2\\-1\end{pmatrix}=1>0
\]

\[
\mathbf{a}(8)^\top=(2\quad -2\quad 1)\quad(\text{无变化})
\]

## 感知机准则

- 结果不唯一且在线性不可分情况下不收敛

![](img/292e77b9b7b40db2ea6f49ac62f8aa0f_231_0.png)

## 最小二乘准则

A.-M. Legendre（1806提出），C. Gauss（1809提出/1829证明）

最小二乘法（最小平方误差法）通过最小化误差的平方和寻找数据的最佳函数匹配，即可以使求得的数据与实际数据之间误差的平方和最小。

![](img/292e77b9b7b40db2ea6f49ac62f8aa0f_232_0.png)

寻找最好投影方向 \(a^*\)

\[
a^T y_n > 0
\]

\[
a^T y_n = b_n > 0
\]

\(b_n\) 是任意给定的正常数。

方程组形式：

\[
Y a = b
\]

\[
Y = \begin{bmatrix} y_1^T \\ y_2^T \\ \vdots \\ y_N^T \end{bmatrix} = \begin{bmatrix} y_{11} & y_{12} & \cdots & y_{1\hat{d}} \\ y_{21} & y_{22} & \cdots & y_{2\hat{d}} \\ \cdots & \cdots & \cdots & \cdots \\ y_{N1} & y_{N2} & \cdots & y_{N\hat{d}} \end{bmatrix}
\]

\(y_n\) 是规范化增广向量样本；\(Y\) 是 \(N \times \hat{d}\) 维矩阵，通常 \(N > \hat{d}\)，一般为列满秩阵。

\[
b = [b_1 \quad b_2 \quad \cdots \quad b_N]
\]

\(b\) 是 \(N\) 维向量，\(b_n > 0\)，\(n=1,2,...,N\)。

方程数多于未知数的矛盾方程组通常没有精确解。

定义误差向量：\(e = Y a - b\) 及平方误差准则函数

\[
J_S(a) = \|e\|^2 = \|Y a - b\|^2 = \sum_{n=1}^{N} (a^T y_n - b_n)^2
\]

求使 \(J_S(a)\) 最小的 \(a^*\)（最小二乘近似解/伪逆解/MSE解）。

采用解析法求伪逆解：

\[
J_S(a)=\|e\|^2=\|Ya-b\|^2=\sum_{n=1}^{N}(a^T y_n-b_n)^2
\]

\[
\nabla J_S(a)=\sum_{n=1}^{N}2(a^T y_n-b_n)y_n=2Y^T(Ya-b)
\]

令 \(\nabla J_S(a)=0\)，得

\[
Y^TYa^*=Y^Tb
\]

矩阵 \(Y^TY\) 是 \(d\times d\) 方阵，一般非奇异。

唯一解：

\[
a^*=(Y^TY)^{-1}Y^Tb=Y^+b
\]

其中 \(d\times N\) 矩阵 \(Y^+=(Y^TY)^{-1}Y^T\) 是 \(Y\) 的左逆矩阵。

如何选 \(b\)？

\[
b=\begin{bmatrix}N/N_1\\ \vdots\\ N/N_1\\ N/N_2\\ \vdots\\ N/N_2\end{bmatrix}
\]

其中前 \(N_1\) 个元素对应一类，后 \(N_2\) 个元素对应另一类。

\(a^*\) 等价于 Fisher 解。

\[
g_0(x)=P(\omega_1|x)-P(\omega_2|x)
\]

当 \(N\to\infty\) 时，取 \(b=[1,1,\cdots,1]^T\)（\(N\) 个），以最小均方误差逼近贝叶斯判别函数。

对异常值(Outlier)非常敏感。

![](img/292e77b9b7b40db2ea6f49ac62f8aa0f_236_0.png)

![](img/292e77b9b7b40db2ea6f49ac62f8aa0f_236_1.png)

## 多分类问题

- 1 对 (N-1) 或 1 对 1

![](img/292e77b9b7b40db2ea6f49ac62f8aa0f_237_0.png)

![](img/292e77b9b7b40db2ea6f49ac62f8aa0f_237_1.png)

## (补) 生成式模型和判别式模型

生成式模型和判别式模型

### 生成式模型（Generative Model）

分别对各类的**类条件密度** \(p(x|C_k)\) 和**先验概率** \(p(C_k)\) 进行建模，之后利用贝叶斯定理计算**后验概率**

\[
p(C_k|x)=\frac{p(x|C_k)p(C_k)}{\sum_j p(x|C_j)p(C_j)}
\]

或者直接对**联合分布** \(p(x,C_k)\) 建模得到后验概率。

### 判别式模型（Discriminative Model）

直接对**后验概率** \(p(C_k|x)\) 建模。

![](img/292e77b9b7b40db2ea6f49ac62f8aa0f_239_0.png)

## 回归和分类

### 线性回归和逻辑回归

**线性模型**

\[
y = \mathbf{w}^T x + w_0
\]

**逻辑模型**

\[
p = \frac{1}{1 + e^{-(\mathbf{w}^T x + w_0)}}
\]

## 逻辑回归(Logistic Regression)

### 将回归问题转为分类问题

逻辑回归是概率型非线性回归，但其本质是线性回归，只是在特征到结果的映射中加入了一层函数映射，即先把特征线性求和，然后使用函数 \(\sigma(z)\) 来预测。

对于二分类：

\[
p(C_1|x)=\frac{p(x|C_1)p(C_1)}{p(x|C_1)p(C_1)+p(x|C_2)p(C_2)}=\frac{1}{1+\exp(-a)}=\sigma(a)
\]

\[
a=\ln\frac{p(x|C_1)p(C_1)}{p(x|C_2)p(C_2)}
\]

### Sigmoid函数性质

- ① 可以将连续值映射到0和1区间上
- ② 对称性：\(\sigma(-a)=1-\sigma(a)\)
- ③ 反转性：\(a=\ln(\sigma/(1-\sigma))\)
- ④ 可导性：\(\frac{d\sigma}{da}=\sigma(1-\sigma)\)

![](img/292e77b9b7b40db2ea6f49ac62f8aa0f_241_0.png)

### 多类问题

\[
p(C_k|x)=\frac{p(x|C_k)p(C_k)}{\sum_j p(x|C_j)p(C_j)}=\frac{\exp(a_k)}{\sum_j \exp(a_j)}
\]

\[
a_k=\ln p(x|C_k)p(C_k)
\]

**归一化指数（Normalized Exponential）**，即 **Softmax 函数**。它是一个平滑的 max 函数：对于所有的 \(k \neq j\)，如果 \(a_k \gg a_j\)，有 \(p(C_k|x) \approx 1\)，\(p(C_j|x) \approx 0\)。

## 生成式模型和判别式模型

对于二分类情形：

\[
p(C_1|x)=\frac{p(x|C_1)p(C_1)}{p(x|C_1)p(C_1)+p(x|C_2)p(C_2)}=\frac{1}{1+\exp(-a)}=\sigma(a)
\]

\[
a=\ln\frac{p(C_1|x)}{p(C_2|x)}=\ln\frac{p(x|C_1)p(C_1)}{p(x|C_2)p(C_2)}
\]

- **生成式模型（Generative Model）**：估计类条件密度并计算 \(a\)
- **判别式模型（Discriminative Model）**：把 \(a\) 视为线性函数 \(a = \mathbf{w}^T x + w_0\) 直接估计

### 生成式模型

**优点：**
- 信息丰富
- 单类问题灵活性强
- 增量学习
- 合成缺失数据

**缺点：**
- 学习过程复杂
- 为分布牺牲分类性能

**代表算法：**
- Naive Bayes
- Mixtures of Gaussians
- Hidden Markov Models
- Bayesian Networks
- Deep Belief Network

### 判别式模型

**优点：**
- 类间差异清晰
- 分类边界灵活
- 学习简单
- 性能较好

**缺点：**
- 不能反映数据特性
- 需要全部数据进行学习

**代表算法：**
- Linear & Logistic Regression
- Support Vector Machine
- Nearest Neighbor
- Conditional Random Fields
- Boosting

由生成模型可以得到判别模型，但由判别模型得不到生成模型。

![](img/292e77b9b7b40db2ea6f49ac62f8aa0f_245_0.png)

