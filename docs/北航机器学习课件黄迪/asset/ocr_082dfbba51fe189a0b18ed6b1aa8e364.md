# EM算法

● 令

$$B(\theta,\theta^{(i)})=\ell(\theta^{(i)})+\sum_z p(z\mid X,\theta^{(i)})\ln\frac{p(X\mid Z,\theta)p(Z\mid\theta)}{p(Z\mid X,\theta^{(i)})p(X\mid\theta^{(i)})}$$

则

$$\ell(\theta)\ge B(\theta,\theta^{(i)})$$

$B(\theta,\theta^{(i)})$ 是 $\ell(\theta)$ 的一个下界

因此，使 $B(\theta,\theta^{(i)})$ 增大的 $\theta$ 也可以使 $\ell(\theta)$ 增大