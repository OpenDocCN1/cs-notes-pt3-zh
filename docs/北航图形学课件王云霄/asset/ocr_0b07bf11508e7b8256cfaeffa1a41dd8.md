$$P(t)=\sum_{i=0}^{n}\left(P_i\cdot a_{i,0}(t)+P'_i\cdot a_{i,1}(t)\right)$$

每段曲线 $P_i(t)$ 只在 $[t_i,t_{i+1}]$ 中有定义：

$$P_i(t)=P_i\cdot a_{i,0}(t)+P_{i+1}\cdot a_{i+1,0}(t)$$
$$\quad+P'_i\cdot a_{i,1}(t)+P'_{i+1}\cdot a_{i+1,1}(t)$$
$$=P_i\cdot g_{i,0}(t)+P_{i+1}\cdot g_{i,1}(t)$$
$$\quad+[P'_i\cdot h_{i,0}(t)+P'_{i+1}\cdot h_{i,1}(t)](t_{i+1}-t_i)$$