

## 动态表的会计分析

对第 \(i\) 次插入收取摊还成本 \(\hat{c}_i = \$3\)。

- \(\$1\) 支付即时插入。
- \(\$2\) 存储起来以备表加倍时使用。

当表加倍时，\(\$1\) 支付移动一个近期项目，\(\$1\) 支付移动一个旧项目。

### 示例：

![](img/e8cfdb0a049dc5ab9d802234ebc2190e_14_0.png)

![](img/e8cfdb0a049dc5ab9d802234ebc2190e_14_1.png)

![](img/e8cfdb0a049dc5ab9d802234ebc2190e_15_0.png)

![](img/e8cfdb0a049dc5ab9d802234ebc2190e_16_0.png)

![](img/e8cfdb0a049dc5ab9d802234ebc2190e_16_1.png)

## 会计分析（续）

**关键不变量：** 银行余额永不低于 0。因此，摊还成本之和提供了真实成本之和的上界。

| 操作 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | 10 |
|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|
| \(size_i\) | 1 | 2 | 4 | 4 | 8 | 8 | 8 | 8 | 16 | 16 |
| \(c_i\) | 1 | 2 | 3 | 1 | 5 | 1 | 1 | 1 | 9 | 1 |
| \(\hat{c}_i\) | \(2^*\) | 3 | 3 | 3 | 3 | 3 | 3 | 3 | 3 | 3 |
| \(bank_i\) | 1 | 2 | 2 | 4 | 2 | 4 | 6 | 8 | 2 | 4 |

\* 好吧，我撒谎了。第一次操作只花费 \$2，而不是 \$3。

## 理解势能

![](img/e8cfdb0a049dc5ab9d802234ebc2190e_19_0.png)

\[
\hat{c}_i = c_i + \Phi(D_i) - \Phi(D_{i-1})
\]

**势能差** \(\Delta\Phi_i\)

- 如果 \(\Delta\Phi_i > 0\)，则 \(\hat{c}_i > c_i\)。操作 \(i\) 将工作存储在数据结构中以备后用。
- 如果 \(\Delta\Phi_i < 0\)，则 \(\hat{c}_i < c_i\)。数据结构提供存储的工作来帮助支付操作 \(i\)。

## 摊还成本限制真实成本

\(n\) 个操作的摊还总成本为

\[
\sum_{i=1}^{n}\hat{c}_i = \sum_{i=1}^{n}\left(c_i + \Phi(D_i) - \Phi(D_{i-1})\right)
\]

对两边求和。

\[
= \sum_{i=1}^{n}c_i + \Phi(D_n) - \Phi(D_0)
\]

级数 telescoping。

\[
\geq \sum_{i=1}^{n}c_i \qquad \text{since } \Phi(D_n)\geq 0 \text{ and } \Phi(D_0)=0.
\]

![](img/e8cfdb0a049dc5ab9d802234ebc2190e_22_0.png)

## 表加倍的势能分析

定义第 \(i\) 次插入后表的势能为

\[
\Phi(D_i) = 2i - 2^{\lceil\lg i\rceil}.
\]

（假设 \(2^{\lceil\lg 0\rceil}=0\)。）

### 注：

- \(\Phi(D_0)=0\)，
- \(\Phi(D_i)\geq 0\) 对所有 \(i\) 成立。

### 示例：

![](img/e8cfdb0a049dc5ab9d802234ebc2190e_23_0.png)

\[
\Phi = 2\cdot 6 - 2^3 = 4
\]

（会计方法）

## 摊还成本的计算

![](img/e8cfdb0a049dc5ab9d802234ebc2190e_24_0.png)

第 \(i\) 次插入的摊还成本为

\[
\hat{c}_i = c_i + \Phi(D_i) - \Phi(D_{i-1})
\]

\[
= \begin{cases}
i & \text{if } i-1 \text{ is an exact power of 2,}\\
1 & \text{otherwise;}
\end{cases}
+ \left(2i - 2^{\lceil\lg i\rceil}\right) - \left(2(i-1) - 2^{\lceil\lg(i-1)\rceil}\right)
\]

\[
= \begin{cases}
i & \text{if } i-1 \text{ is an exact power of 2,}\\
1 & \text{otherwise;}
\end{cases}
+ 2 - 2^{\lceil\lg i\rceil} + 2^{\lceil\lg(i-1)\rceil}.
\]

### 计算

### 情况 1：\(i-1\) 是 2 的精确幂。

\[
\hat{c}_i = i + 2 - 2^{\lceil\lg i\rceil} + 2^{\lceil\lg(i-1)\rceil}
\]

\[
= i + 2 - 2(i-1) + (i-1)
\]

\[
= i + 2 - 2i + 2 + i - 1
\]

\[
= 3
\]

### 情况 2：\(i-1\) 不是 2 的精确幂。

\[
\hat{c}_i = 1 + 2 - 2^{\lceil\lg i\rceil} + 2^{\lceil\lg(i-1)\rceil}
\]

\[
= 3
\]

因此，\(n\) 次插入在最坏情况下花费 \(\Theta(n)\)。

### 练习：

修复此分析中的错误以表明第一次插入的摊还成本仅为 2。

