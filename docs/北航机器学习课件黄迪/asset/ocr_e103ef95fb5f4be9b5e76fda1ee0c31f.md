# 模型求解

+   - 求解问题：确定参数 $w$
+   - 基本思想：在训练集中最小化预测值 $f$ 与真实值 $y$ 的差异
+   
+   $$J(\mathbf{w}) = \frac{1}{2} \sum_{i=1}^{N} \left(f(\mathbf{x}_i) - y_i\right)^2$$
+   
+   $$\hat{\mathbf{w}} = \arg\min_{\mathbf{w}} J(\mathbf{w}) = \arg\min_{\mathbf{w}} \left[\frac{1}{2} \sum_{i=1}^{N} \left(f(\mathbf{x}_i) - y_i\right)^2\right]$$

确定性方法($w$和$t_n$都是确定量)

$$E(\mathbf{w}) = \frac{1}{2} \sum_{n=1}^{N} \{y(x_n, \mathbf{w}) - t_n\}^2$$

$$\tilde{E}(\mathbf{w}) = \frac{1}{2} \sum_{n=1}^{N} \{y(x_n, \mathbf{w}) - t_n\}^2 + \frac{\lambda}{2} \|\mathbf{w}\|^2$$