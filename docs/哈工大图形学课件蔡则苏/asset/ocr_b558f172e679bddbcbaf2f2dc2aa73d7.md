# # 改进的Bresenham算法——原理

```
$$\begin{cases} x_{i+1}=x_i+1 \\ y_{i+1}=\begin{cases}y_i+1 & (d>0.5) \\ y_i & (d\leq 0.5)\end{cases} \end{cases}$$
```

# ## 误差项的计算

+   - $d_{初}=0$
+   - 每走一步：$d=d+k$
+   - 一旦$y$方向上走了一步，$d=d-1$