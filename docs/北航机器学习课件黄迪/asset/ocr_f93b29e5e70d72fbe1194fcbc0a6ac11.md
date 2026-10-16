# 重要性采样（Importance Sampling）

+   与拒绝采样类似，借助一个容易采样的建议分布 $q(z)$

$\mathbb{E}(f) = \int f(z)p(z)dz$
$= \int f(z)\frac{p(z)}{q(z)}q(z)dz$
$\approx \frac{1}{L}\sum_{l=1}^{L}\frac{p(z^{(l)})}{q(z^{(l)})}f(z^{(l)})$

![](bbox=[0.56, 0.33, 0.97, 0.64])

重要性权重

注：$p(z) = \frac{1}{Z_p}\tilde{p}(z)$