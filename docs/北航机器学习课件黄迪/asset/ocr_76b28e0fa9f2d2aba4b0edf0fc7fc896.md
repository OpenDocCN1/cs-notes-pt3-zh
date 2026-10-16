# 重要性采样（Importance Sampling）

$$\frac{Z_p}{Z_q}=\frac{1}{Z_q}\int \tilde{p}(z)\,dz$$

$$=\int \frac{\tilde{p}(z)}{\tilde{q}(z)}q(z)\,dz$$

$$\approx \frac{1}{L}\sum_{l=1}^{L}\tilde{r}_l$$

$$\mathbb{E}(f)\approx\sum_{l=1}^{L}w_l f\left(z^{(l)}\right)$$

$$w_l=\frac{\tilde{r}_l}{\sum_m\tilde{r}_m}=\frac{\tilde{p}\left(z^{(l)}\right)/q\left(z^{(l)}\right)}{\sum_m \tilde{p}\left(z^{(m)}\right)/q\left(z^{(m)}\right)}$$