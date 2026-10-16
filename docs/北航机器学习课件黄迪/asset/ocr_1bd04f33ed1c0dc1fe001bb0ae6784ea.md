# 与M-H的关系

+   建议概率：
+   $q_k(\mathbf{z}^*|\mathbf{z}) = p(z_k^*|\mathbf{z}_{\setminus k})$

+   接受概率：
+   $A_k(z^*, z^{(\tau)}) = \min\left\{1, \frac{\tilde{p}(z^*) q_k(z^{(\tau)}|z^*)}{\tilde{p}(z^{(\tau)}) q_k(z^*|z^{(\tau)})}\right\}$

$p(\mathbf{z}) = p(z_k|\mathbf{z}_{\setminus k})p(\mathbf{z}_{\setminus k}) \quad \mathbf{z}^*_{\setminus k} = \mathbf{z}_{\setminus k}$

$A(\mathbf{z}^*, \mathbf{z}) = \frac{p(\mathbf{z}^*) q_k(\mathbf{z}|\mathbf{z}^*)}{p(\mathbf{z}) q_k(\mathbf{z}^*|\mathbf{z})} = \frac{p(z_k^*|\mathbf{z}^*_{\setminus k})p(\mathbf{z}^*_{\setminus k})p(z_k|\mathbf{z}^*_{\setminus k})}{p(z_k|\mathbf{z}_{\setminus k})p(\mathbf{z}_{\setminus k})p(z_k^*|\mathbf{z}_{\setminus k})} = 1$