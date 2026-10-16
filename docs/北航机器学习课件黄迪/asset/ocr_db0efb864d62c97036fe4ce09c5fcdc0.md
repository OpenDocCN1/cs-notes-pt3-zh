# # 拒绝采样（Rejection Sampling）

+   - 找到一个常数 $k$，使得 $\tilde{p}(z) \leq kq(z)$ —— 对比函数 comparison function
+   - 采样步骤
+     1. 从 $q(z)$ 中产生 $z_0$
+     2. 从 $[0,kq(z_0)]$ 均匀分布中产生 $u_0$
+     3. 如果 $u_0 > \tilde{p}(z_0)$ 拒绝采样，否则接受采样

![](bbox=[0.457, 0.324, 0.994, 0.738])

$p(\mathrm{accept})=\int\{\tilde{p}(z)/kq(z)\}q(z)\,dz=\frac{1}{k}\int\tilde{p}(z)\,dz$

拒绝采样又称为接受-拒绝采样（Acceptance-Rejection Sampling）