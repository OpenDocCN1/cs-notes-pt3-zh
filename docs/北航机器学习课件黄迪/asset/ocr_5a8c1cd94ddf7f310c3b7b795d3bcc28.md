# 循环神经网络（Recurrent neural Network，RNN）

+   - RNN中gradient vanishing/exploding
+     - 已知 \(\frac{\partial h_t}{\partial h_k}=\prod_{j=k+1}^{t}\frac{\partial h_j}{\partial h_{j-1}}=\prod_{j=k+1}^{t}W^T\operatorname{diag}[f'(h_{j-1})]\)
+     - 根据 \(\|xy\|\leq\|x\|\cdot\|y\|\)

\(\left\|\frac{\partial h_j}{\partial h_{j-1}}\right\|\leq\|W^T\|\|\operatorname{diag}[f'(h_{j-1})]\|\leq\beta_W\beta_h\)　代表上限

\(\left\|\frac{\partial h_t}{\partial h_k}\right\|=\left\|\prod_{j=k+1}^{t}\frac{\partial h_j}{\partial h_{j-1}}\right\|\leq(\beta_W\beta_h)^{t-k}\)

当\(t\)为间隔较远时，梯度会很快的变的很大或很小