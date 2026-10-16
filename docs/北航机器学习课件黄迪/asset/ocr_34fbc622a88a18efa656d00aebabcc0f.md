# Slice Sampling

$\hat{p}(z,u)=\begin{cases}1/Z_p & \text{if }0\le u\le \tilde{p}(z)\\0 & \text{otherwise}\end{cases}\qquad \int \hat{p}(z,u)\,du\int_{0}^{\tilde{p}(z)}\frac{1}{Z_p}\,du=\frac{\tilde{p}(z)}{Z_p}=p(z)$

+   - **第一步：** 给定 $z$，在 $0\le u\le \tilde{p}(z)$ 范围内均匀分布产生 $u$
+   - **第二步：** 给定 $u$，在 $\{z:\tilde{p}(z)>u\}$ 范围内均匀分布产生 $z$

![](bbox=[0.324, 0.616, 0.81, 0.977])