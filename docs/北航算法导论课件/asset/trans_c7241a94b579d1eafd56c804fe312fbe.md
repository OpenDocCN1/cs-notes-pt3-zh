

## 30.2.1 复数单位根
### 一些性质
1) \(\omega_n^n=\omega_n^0=1\)

\(\left(\omega_n=e^{2\pi i/n}=\cos 2\pi+i\sin 2\pi\right)\)

2) \(\omega_n^j\omega_n^k=\omega_n^{j+k}=\omega_n^{(j+k)\bmod n}\)

\(\text{(if }j+k=mn+r,\text{ then}\)

\(\omega_n^{j+k}=\omega_n^{mn+r}=\omega_n^{mn}\omega_n^r=(\omega_n^n)^m\omega_n^r=\omega_n^r=\omega_n^{(j+k)\bmod n}\text{)}\)

3) \(\omega_n^{-1}=\omega_n^{n-1}\)

(使用 \(\omega_n^k=e^{2\pi ik/n},\ k=0,1,\cdots,n-1\) 证明)

![](img/09c68ab421cfce4995ddad1430ef2637_511_0.png)

## 30.2.1 复数单位根
### 引理 30.3 (消去引理，可约（相消）引理)
对于任意整数 n≥0, k≥0, 和 d >0,

ω_{dn}^{dk} = ω_n^{k}.  (30.7)

证明  ω_{dn}^{dk} = (e^{2πi / dn})^{dk} = (e^{2πi / n})^{k} = ω_n^{k}.

( ω_8^2 = ω_4^1,   ω_8^4 = ω_4^2,   ω_8^6 = ω_4^3,   ω_8^8 = ω_4^4 )

### 推论 (推论) 30.4 对于任意偶数整数 n>0,

ω_n^{n/2} = ω_2 = -1.

ω_n^{n/2} = ω_{(n/2)·2}^{n/2} = ω_2 = e^{2πi /2} = cos π + i sin π = -1.

![](img/09c68ab421cfce4995ddad1430ef2637_512_0.png)

## 30.2.1 复数单位根
### 引理 30.5 (二分引理，等分引理)

如果 n > 0 为偶数，则 n 个复数 n 次单位根的平方是 n/2 个复数 n/2 次单位根。

〔n 个单位 n 次复方根的平方是 n/2 个 n/2 次复方根〕

### 证明思路

(ωₙᵏ)² = ω₂₍ₙ/₂₎²ᵏ = ωₙ/₂ᵏ , k = 0,1,…, n/2 −1

(ωₙᵏ⁺ⁿ/₂)² = ωₙ²ᵏ⁺ⁿ = ωₙ²ᵏ ωₙⁿ = ωₙ²ᵏ = (ωₙᵏ)² = ωₙ/₂ᵏ , k = 0,1,…, n/2 −1

![](img/09c68ab421cfce4995ddad1430ef2637_513_0.png)

(ωₙ⁰)² , (ωₙ¹)² , … , (ωₙⁿ/₂⁻¹)²
(ωₙ⁰⁺ⁿ/₂)² , (ωₙ¹⁺ⁿ/₂)² , … , (ωₙⁿ/₂⁻¹⁺ⁿ/₂)²

ωₙ/₂⁰ , ωₙ/₂¹ , … , ωₙ/₂ⁿ/₂⁻¹

![](img/09c68ab421cfce4995ddad1430ef2637_513_1.png)

-3, -2, -1, 1, 2, 3

9, 4, 1

![](img/09c68ab421cfce4995ddad1430ef2637_513_2.png)

## 30.2.1 复数单位根
### 引理 30.6 (求和引理，求和引理)

对于任意整数 $n\ge1$ 和非负整数 $k$ 不能被 $n$ 整除，$(k \ne m\cdot n)$，我们有

$$\sum_{j=0}^{n-1} (\omega_n^k)^j = 0.$$

### 证明

$$\sum_{j=0}^{n-1} (\omega_n^k)^j = \frac{(\omega_n^k)^n - 1}{\omega_n^k - 1} = \frac{(\omega_n^n)^k - 1}{\omega_n^k - 1} = \frac{(1)^k - 1}{\omega_n^k - 1} = 0,\ k \ne mn.$$

（证明思想：利用实数的等幂级数求和性质）

## 30.2.2 离散傅里叶变换
- 希望求值多项式 $A(x)=\sum_{j=0}^{n-1} a_j x^j$ 的次数上界为 $n$ 在 $x = \omega_n^0, \omega_n^1, \omega_n^2, \cdots, \omega_n^{n-1}$ 处的值。
- 在不失一般性的情况下，假设 $n=2^m$，如果不是，则令 $a_{n+k}=0$
- 离散傅里叶变换 (DFT, 离散傅里叶变换)
  设 $A$ 以系数形式给出：$a=(a_0, a_1, ..., a_{n-1})^T$，令 $x_k = \omega_n^k$，定义 $y_k$，对于 $k = 0, 1, ..., n-1$，为
- $y_k = A(\omega_n^k) = \sum_{j=0}^{n-1} a_j \omega_n^{kj}$, $
- $\begin{pmatrix} y_0 \\ y_1 \\ \vdots \\ y_{n-1} \end{pmatrix} = 
- $\begin{pmatrix} 1 & 1 & 1 & \cdots & 1 \\ 1 & \omega_n^1 & \omega_n^2 & \cdots & \omega_n^{n-1} \\ \vdots & \vdots & \vdots & \ddots & \vdots \\ 1 & \omega_n^{(n-1)1} & \omega_n^{(n-1)2} & \cdots & \omega_n^{(n-1)(n-1)} \end{pmatrix} 
- $\begin{pmatrix} a_0 \\ a_1 \\ \vdots \\ a_{n-1} \end{pmatrix}$
- 也写成 $y = \text{DFT}_n(a)$。
- 直接计算需要 $\Theta(n^2)$ 时间？（不好！）

## 30.2.3 快速傅里叶变换
A(x) = a₀ + a₁x + a₂x² + a₃x³ + ⋯ + aₙ₋₁xⁿ⁻¹

- **快速傅里叶变换 (FFT, 快速傅里叶变换)**
- 利用复数单位根的特殊性质
- 我们可以在 $\Theta(n \log n)$ 时间内计算 DFTₙ(a)
- 采用分治策略，
  偶数下标，A^[0](x) = a₀ + a₂x + a₄x² + ... + aₙ₋₂xⁿ/²⁻¹
  奇数下标，A^[1](x) = a₁ + a₃x + a₅x² + ... + aₙ₋₁xⁿ/²⁻¹。
- A[0] 包含 A 的所有偶数下标系数（下标的二进制表示以 0 结尾）
- A[1] 包含所有奇数下标系数（下标的二进制表示以 1 结尾）。由此可得

A(x) = A^[0](x²) + x A^[1](x²)    (30.9)

## 30.2.3 快速傅里叶变换
- 快速傅里叶变换 (FFT, 快速傅里叶变换)
- 采用分治策略，
  偶数下标，$A^{[0]}(x) = a_0 + a_2 x + a_4 x^2 + ... + a_{n-2} x^{n/2-1}$
  奇数下标，$A^{[1]}(x) = a_1 + a_3 x + a_5 x^2 + ... + a_{n-1} x^{n/2-1}$.
  $A(x) = A^{[0]}(x^2) + x A^{[1]}(x^2)$  (30.9)
  $A(\omega_n^k) = A^{[0]}((\omega_n^k)^2) + \omega_n^k A^{[1]}((\omega_n^k)^2)$

$A(x) = \sum_{j=0}^{n-1} a_j x^j$

- 求值 $A(x)$ 在 $\omega_n^0, \omega_n^1, \omega_n^2, ..., \omega_n^{n-1}$ 处的问题归结为
  1) 求 $A^{[0]}(x)$ 和 $A^{[1]}(x)$ 在点
     $(\omega_n^0)^2, (\omega_n^1)^2, ..., (\omega_n^{n/2-1})^2$
     $(\omega_n^{0+n/2})^2, (\omega_n^{1+n/2})^2, ..., (\omega_n^{n/2-1+n/2})^2$
     处的值
     以及 $\omega_{n/2}^0, \omega_{n/2}^1, ..., \omega_{n/2}^{n/2-1}$  (32.10)
  2) 根据公式 (30.9) 合并结果。

