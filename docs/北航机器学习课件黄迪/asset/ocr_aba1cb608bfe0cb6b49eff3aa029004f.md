# Metropolis-Hastings 方法

+   在细致平稳条件两边乘以因子 $C$

$p(z)q(z'|z)a(z,z') \cdot C = p(z')q(z|z')a(z',z) \cdot C$

细致平稳条件并没有打破！！！

+   同比例放大 $a(z,z')$, $a(z',z)$ 使最大的为1, 令

$A(z,z') = \min\left\{1, \frac{p(z)q(z'|z)}{p(z')q(z|z')}\right\}$

$= \min\left\{1, \frac{\tilde p(z)q(z'|z)}{\tilde p(z')q(z|z')}\right\} \quad p(z) = \frac{1}{Z_p}\tilde p(z)$