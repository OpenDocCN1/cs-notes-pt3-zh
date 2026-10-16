# # 基本采样法（Basic Sampling）

+   - **高斯分布：**

$z_1,z_2\sim U(0,1)$

$p(z_1,z_2)=1,\quad (z_1+z_2)^2\le 1$

$y_1=\sqrt{-2\ln z_1}\cos(2\pi z_2)$

$y_2=\sqrt{-2\ln z_1}\sin(2\pi z_2)$

> > 不适用于积分及反函数难求的分布！

$r^2=(z_1+z_2)^2$

$p(y_1,y_2)=p(z_1,z_2)\left|\frac{\partial(z_1,z_2)}{\partial(y_1,y_2)}\right|$

$=\left[\frac{1}{\sqrt{2\pi}}\exp(-y_1^2/2)\right]\left[\frac{1}{\sqrt{2\pi}}\exp(-y_2^2/2)\right]$

**Box-Muller变换**