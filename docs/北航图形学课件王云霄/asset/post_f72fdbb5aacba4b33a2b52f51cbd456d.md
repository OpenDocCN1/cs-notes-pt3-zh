
## 4.曲线段间 $C^1, C^2$ 和 $G^1, G^2$ 连续性定义

- (1) Q1(1)=Q2(0),则Q1(t)和Q2(t)在P处有 $C^0$ 和 $G^0$ 连续性
- (2) Q1(1)和Q2(0) 在P处重合，且其在P点处的切矢量方向相同，大小不等，则Q1(t)和Q2(t)在P处有 $G^1$ 连续性
- (3) Q1(1)和Q2(0) 在P处重合，且其在P点处的切矢量方向相同，大小相等，则Q1(t)和Q2(t)在P处有 $C^1$ 连续性
- (4) Q1(1)和Q2(0) 在P处已有 $C^0, C^1$ 连续 且 $Q_1''(1) and Q_2''(0)$ 大小方向均相同，则Q1(t)和Q2(t)在P处有 $C^2$ 连续性

推广之，Q1(1)和Q2(0) 在P处 $∈ C^0, C^1 … C^n$ 连续，若 $Q_1'' and Q_2''$ 在P处大小和方向均相同，则说Q1(t) 和Q2(t)在P处具有 $C^n$ 连续性

(5). Q1(1)和Q2(0)在P处已有 $G^0,G^1$ 连续 且 $Q_1''(1)$ 和 $Q_2''(0)$ 方向相同但大小不等，则Q1(t)和Q2(t)在P处有 $G^2$ 连续性

## 5. 光顺

光顺（smoothness）是指曲线的拐点不能太多，要光滑顺畅。对于平面曲线相对光顺的条件应该是： （1）具有二阶几何连续（$G^2$）；（2）不存在多余拐点和奇异点；（3）曲率变化较小

## 第二节 Hermite多项式

已知函数 $f(t)$ 在 $k+1$ 个点 $\{t_i\}$ 处的函数值和导数值 $\{f^{(j)}(t_i)\}$，$j=0,1,\ldots,k$，$i=0,1,\ldots,m_i-1$，要求确定一个 $N=m_0+m_1+\cdots+m_k-1$ 次的多项式 $P(t)$，满足下面的插值条件：

$$P^{(j)}(t_i)=f^{(j)}(t_i)$$

## 1. Lagrange插值法(m₀ = m₁ = ⋯ = mₖ = 1)

已知f(t)在k+1个点的函数值f(tᵢ),求一个k次多项式使p(tᵢ)=f(tᵢ)

p(t) = Σᵢ₌₀ᵏ f(tᵢ)·lᵢ

lᵢ(t) = [(t - t₀)⋯(t - tᵢ₋₁)·(t - tᵢ₊₁)⋯(t - tₖ)] / [(tᵢ - t₀)⋯(tᵢ - tᵢ₋₁)·(tᵢ - tᵢ₊₁)⋯(tᵢ - tₖ)]

⎧ 1      t = tᵢ
⎨ 0   t = tⱼ, j ≠ i   调和函数

## 混合函数如下：

$$ \begin{cases} l_0(t)=\dfrac{(t-t_1)(t-t_2)}{(t_0-t_1)(t_0-t_2)} \\ l_1(t)=\dfrac{(t-t_0)(t-t_2)}{(t_1-t_0)(t_1-t_2)} \\ l_2(t)=\dfrac{(t-t_0)(t-t_1)}{(t_2-t_0)(t_2-t_1)} \end{cases}$$

## 2.

k = 1, m₀ = m₁ = 2, t ∈ [t₀, t₁]

已知表示一条曲线的某个函数 f(t) 在两点 t₀, t₁ 的函数值 f(t₀), f(t₁) 和一阶导数值 f′(t₀), f′(t₁)，求三次多项式 P(t)：

P(t)=a₃ t³ + a₂ t² + a₁ t + a₀    t ∈ [t₀, t₁]

P(t₀) = f(t₀), P(t₁) = f(t₁),

P′(t₀) = f′(t₀), P′(t₁) = f′(t₁)

## 把a₀，a₁，a₂和a₃代入则有：

P(t) = f(t₀)·[(t−t₁)²(−2t+3t₀−t₁)]/(t₀−t₁)³
+ f(t₁)·[(t−t₀)²(−2t+3t₁−t₀)]/(t₁−t₀)³ + f′(t₀)·[(t−t₁)²(t−t₀)]/(t₁−t₀)²
+ f′(t₁)·[(t−t₀)²(t−t₁)]/(t₁−t₀)²      t ∈ [t₀, t₁]

## 经整理，所求多项式P₀(t)
可以写出如下：

P₀(t) = f(t₀)·g₀₀(t) + f(t₁)·g₀₁(t)
+ f'(t₀)·h₀₀(t)·(t₁ − t₀) + f'(t₁)·h₀₁(t)·(t₁ − t₀)

式中选取两个端点及其及其切向量作为曲线构造条件
混合函数如下：

$$ \begin{cases} g_{00}(t)=\left(1-2\cdot\frac{t-t_0}{t_0-t_1}\right)\cdot\left(\frac{t-t_1}{t_0-t_1}\right)^2 \\ g_{01}(t)=\left(1-2\cdot\frac{t-t_1}{t_1-t_0}\right)\cdot\left(\frac{t-t_0}{t_1-t_0}\right)^2 \\ h_{00}(t)=\left(\frac{t-t_0}{t_1-t_0}\right)\cdot\left(\frac{t-t_1}{t_0-t_1}\right)^2 \\ h_{01}(t)=\left(\frac{t-t_1}{t_1-t_0}\right)\cdot\left(\frac{t-t_0}{t_1-t_0}\right)^2 \end{cases}$$

经验可知：

\begin{cases} g_{00}(t_0)=1 \\ g_{01}(t_0)=0 \\ h_{00}(t_0)=0 \\ h_{01}(t_0)=0 \end{cases}

\begin{cases} g_{00}(t_1)=0 \\ g_{01}(t_1)=1 \\ h_{00}(t_1)=0 \\ h_{01}(t_1)=0 \end{cases}

\begin{cases} g'_{00}(t_0)=0 \\ g'_{01}(t_0)=0 \\ h'_{00}(t_0)=\frac{1}{t_1-t_0} \\ h'_{01}(t_0)=0 \end{cases}

\begin{cases} g'_{00}(t_1)=0 \\ g'_{01}(t_1)=0 \\ h'_{00}(t_1)=0 \\ h'_{01}(t_1)=\frac{1}{t_1-t_0} \end{cases}

## 3.

t ∈ [t₀, t₁] → u ∈ [0,1]

为了使P₀(t)的定义区间 t₀ ≤ t ≤ t₁ 变为区间 0 ≤ u ≤ 1，可以做如下变换

```
u = (t - t₀) / (t₁ - t₀)
```

解出 t = t₀ + (t₁ - t₀)u，代入混合函数式中，得：

g₀₀(t) = g₀₀(t₀ + (t₁ - t₀)u)
=(1+2u)(u-1)²
=2u³ -3u² +1 = q₀₀(u)
g₀₁(t) = g₀₁(t₀ + (t₁ - t₀)u)
=(3-2u)u²
= -2u³ +3u² = q₀₁(u)

h_{00}(t)=h_{00}(t_0+(t_1-t_0)u)
=u(1-u)^2
=u^3-2u^2+u=q_{10}(u)
h_{01}(t)=h_{01}(t_0+(t_1-t_0)u)
=(-1+u)u^2
=u^3-u^2=q_{11}(u)

## 将关于 $u$ 的混合函数代入，所求的三次多项式成为：

$$\tilde{f}(u)=\tilde{P}_0(u)=P_0\bigl(t_0+(t_1-t_0)u\bigr)$$

$$=f(t_0)\cdot q_{00}(u)+f(t_1)\cdot q_{01}(u)$$

$$+f'(t_0)\cdot(t_1-t_0)\cdot q_{10}(u)$$

$$+f'(t_1)\cdot(t_1-t_0)\cdot q_{11}(u)$$

令

$\tilde{f}(0)=f(t_0)$

$\tilde{f}(1)=f(t_1)$

$\tilde{f}'(0)=f'(t_0)(t_1-t_0)$

$\tilde{f}'(1)=f'(t_1)(t_1-t_0)$

## 得

$$\widetilde{P}_0(u)=\widetilde{f}(0)\cdot q_{00}(u)+\widetilde{f}(1)\cdot q_{01}(u)$$
$$\qquad\quad+\widetilde{f}'(0)\cdot q_{10}(u)+\widetilde{f}'(1)\cdot q_{11}(u)$$

$$=(q_{00}(u)\quad q_{01}(u)\quad q_{10}(u)\quad q_{11}(u))\begin{bmatrix}\widetilde{f}(0)\\\widetilde{f}(1)\\\widetilde{f}'(0)\\\widetilde{f}'(1)\end{bmatrix}$$
