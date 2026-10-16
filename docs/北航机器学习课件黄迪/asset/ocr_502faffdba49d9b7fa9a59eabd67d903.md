# # 如何有效训练深度神经网络

+   - **Momentum update**
+     - 引入 momentum，使梯度方向具有一定的“惯性”

$$\Delta E'(\mathbf{w}^{\tau})=\rho\Delta E(\mathbf{w}^{\tau-1})+\Delta E(\mathbf{w}^{\tau})$$

$$\mathbf{w}^{(\tau+1)}=\mathbf{w}^{\tau}+\eta\Delta E'(\mathbf{w}^{\tau})$$

![](bbox=[0.128, 0.641, 0.481, 0.836])

![](bbox=[0.566, 0.641, 0.925, 0.836])