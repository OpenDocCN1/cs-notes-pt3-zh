
## K均值过程示例

![](img/292e77b9b7b40db2ea6f49ac62f8aa0f_570_0.png)

## K均值过程示例

![](img/292e77b9b7b40db2ea6f49ac62f8aa0f_571_0.png)

## K均值过程示例

![](img/292e77b9b7b40db2ea6f49ac62f8aa0f_572_0.png)

## 混合高斯模型

- x从第k个高斯采样的概率是
  $$p(x|z_k = 1) = \mathcal{N}(x|\mu_k, \Sigma_k)$$

- x和z的联合分布是
  $$p(x, z) = p(z) \cdot p(x|z)$$

$$p(x) = \sum_{z} p(z) p(x|z) = \sum_{k=1}^{K} \pi_k \mathcal{N}(x|\mu_k, \Sigma_k)$$

## 混合高斯模型

- ● N个样本的联合分布

```
p(X|π, μ, Σ) = ∏_{n=1}^N p(x_n|π, μ, Σ) → 似然函数
```

```
= ∏_{n=1}^N ∑_{k=1}^K π_k N(x_n|μ_k, Σ_k)
```

- ● 两边取对数

```
ln p(X|π, μ, Σ) = ∑_{n=1}^N ln { ∑_{k=1}^K π_k N(x_n|μ_k, Σ_k) }
```

## 混合高斯模型的最大似然估计

- 给定 {x₁, …, x_N} ，估计混合高斯模型参数

```
ln p(X|π, μ, Σ) = Σ_{n=1}^{N} ln { Σ_{k=1}^{K} π_k N(x_n | μ_k, Σ_k) }
```

![](img/292e77b9b7b40db2ea6f49ac62f8aa0f_575_0.png)

奇异问题；
而且解不唯一 K！

## EM算法求解混合高斯问题

```
ln p(X|π, μ, Σ) = Σ_{n=1}^{N} ln { Σ_{k=1}^{K} π_k N(x_n | μ_k, Σ_k) }
```

直接求解该最大似然估计较难

但它的解一定满足以下条件：

对 μ_k 求导

```
0 = - Σ_{n=1}^{N} [ π_k N(x_n | μ_k, Σ_k) / Σ_j π_j N(x_n | μ_j, Σ_j) ] Σ_k (x_n - μ_k)
```

γ(z_nk)

x_n 属于第K个高斯的概率

## # 混合高斯模型

$\gamma(z_k) \equiv p(z_k=1\mid\mathbf{x})$

$=\frac{p(z_k=1)p(\mathbf{x}\mid z_k=1)}{\sum_{j=1}^{K}p(z_j=1)p(\mathbf{x}\mid z_j=1)}$

$=\frac{\pi_k\mathcal{N}(\mathbf{x}\mid\boldsymbol{\mu}_k,\boldsymbol{\Sigma}_k)}{\sum_{j=1}^{K}\pi_j\mathcal{N}(\mathbf{x}\mid\boldsymbol{\mu}_j,\boldsymbol{\Sigma}_j)}$

## EM算法求解混合高斯问题

ln p(X|π, μ, Σ) = Σ_{n=1}^N ln { Σ_{k=1}^K π_k N(x_n | μ_k, Σ_k) }

对 μ_k 求导

μ_k = (1 / N_k) Σ_{n=1}^N γ(z_nk) x_n   N_k = Σ_{n=1}^N γ(z_nk)

第k个高斯所包含的样本数

## EM算法求解混合高斯问题

ln p(X|π, μ, Σ) = Σ_{n=1}^N ln { Σ_{k=1}^K π_k N(x_n|μ_k, Σ_k) }

对 Σ_k 求导

Σ_k = (1/N_k) Σ_{n=1}^N γ(z_nk) (x_n - μ_k)(x_n - μ_k)^T

对 π_k 求导

必须考虑一个约束条件 Σ_{k=1}^K π_k = 1

ln p(X|π, μ, Σ) + λ( Σ_{k=1}^K π_k - 1 )

0 = Σ_{n=1}^N [ N(x_n|μ_k, Σ_k) / Σ_j π_j N(x_n|μ_j, Σ_j) ] + λ

λ = -N

N_k = Σ_{n=1}^N [ π_k N(x_n|μ_k, Σ_k) / Σ_j π_j N(x_n|μ_j, Σ_j) ]

π_k = N_k / N

## EM算法求解混合高斯问题

μ_k = (1/N_k) Σ_{n=1}^N γ(z_nk) x_n    N_k = Σ_{n=1}^N γ(z_nk)

Σ_k = (1/N_k) Σ_{n=1}^N γ(z_nk) (x_n - μ_k)(x_n - μ_k)^T

π_k = N_k / N

γ(z_nk) = [π_k N(x_n | μ_k, Σ_k)] / [Σ_j π_j N(x_n | μ_j, Σ_j)]

## EM算法求解混合高斯问题

# EM for Gaussian Mixtures

Given a Gaussian mixture model, the goal is to maximize the likelihood function with respect to the parameters (comprising the means and covariances of the components and the mixing coefficients).

- 1. Initialize the means μ_k, covariances Σ_k and mixing coefficients π_k, and evaluate the initial value of the log likelihood.
- 2. E step. Evaluate the responsibilities using the current parameter values

γ(z_nk) = π_k N(x_n | μ_k, Σ_k) / Σ_{j=1}^K π_j N(x_n | μ_j, Σ_j). (9.23)

## EM算法求解混合高斯问题

3. M step. Re-estimate the parameters using the current responsibilities

μ_k^{new} = (1/N_k) Σ_{n=1}^{N} γ(z_{nk}) x_n  (9.24)

Σ_k^{new} = (1/N_k) Σ_{n=1}^{N} γ(z_{nk}) (x_n - μ_k^{new}) (x_n - μ_k^{new})^T  (9.25)

π_k^{new} = N_k / N  (9.26)

where

N_k = Σ_{n=1}^{N} γ(z_{nk}).  (9.27)

## EM算法求解混合高斯问题

![](img/292e77b9b7b40db2ea6f49ac62f8aa0f_583_0.png)

## EM算法求解混合高斯问题

![](img/292e77b9b7b40db2ea6f49ac62f8aa0f_584_0.png)

## EM算法求解混合高斯问题

![](img/292e77b9b7b40db2ea6f49ac62f8aa0f_585_0.png)

## EM算法求解混合高斯问题

![](img/292e77b9b7b40db2ea6f49ac62f8aa0f_586_0.png)

## EM算法求解混合高斯问题

![](img/292e77b9b7b40db2ea6f49ac62f8aa0f_587_0.png)

## EM算法求解混合高斯问题

![](img/292e77b9b7b40db2ea6f49ac62f8aa0f_588_0.png)

## EM算法

- ● Jens

如果

当且

则

立

![](img/292e77b9b7b40db2ea6f49ac62f8aa0f_589_0.png)

## EM算法

• 假设有一组数据 $X=\{X_1,\cdots,X_N\}$，经隐变量 $Z$ 产生，该数据的对数似然函数可以写作：

$\ell(\theta)=\ln p(X;\theta)=\ln\sum_Z p(X,Z\mid\theta)$

$=\ln\sum_Z p(X\mid Z,\theta)p(Z\mid\theta)$

式中含有和（或积分）的对数，优化困难

## EM算法

- • 要最大化 $\ell(\theta)$，可以考虑利用迭代的方式，每一个新的 $\theta$ 能使 $\ell(\theta)$ 变大，即 $\ell(\theta) > \ell(\theta^{(i)})$ 为此，考虑两者的差：

$\ell(\theta) - \ell(\theta^{(i)}) = \ln \sum_{Z} p(X|Z,\theta)p(Z|\theta) - \ln p(X;\theta^{(i)})$
