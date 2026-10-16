# # 常见激活函数

# • ReLu家族

$$\mathrm{ReLU}(x)=\begin{cases}x,&x\geq 0\\0,&x<0\end{cases}$$

$$=\max(0,x)$$

$$\mathrm{LeakyReLU}(x)=\begin{cases}x,&x>0\\\gamma x,&x\leq 0\end{cases}$$

$$=\max(0,x)+\gamma\min(0,x)$$

$$\mathrm{PReLU}_i(x)=\begin{cases}x,&x>0\\\gamma_i x,&x\leq 0\end{cases}$$

$$=\max(0,x)+\gamma_i\min(0,x)$$

$$\mathrm{ELU}(x)=\begin{cases}x,&x>0\\\alpha(\exp(x)-1),&x\leq 0\end{cases}$$

$$=\max(0,x)+\min(0,\alpha(\exp(x)-1))$$

$$\mathrm{softplus}(x)=\log(1+\exp(x))$$

![](bbox=[0.383, 0.285, 0.844, 0.794])

▶ 死亡ReLU问题（Dying ReLU Problem）

+   - 计算上更加高效。
+   - 生物上的解释性
+     - 单侧抑制、宽兴奋边界
+   - 在一定程度上缓解梯度消失问题