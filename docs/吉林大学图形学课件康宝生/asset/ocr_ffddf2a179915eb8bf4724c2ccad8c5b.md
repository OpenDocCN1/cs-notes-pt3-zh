# 4. 修正弦长参数化

\begin{cases}
t_0 = 0\\
t_i = t_{i-1} + K_i |\Delta P_{i-1}|,\ i=1,2,\cdots,n
\end{cases}

其中：

K_i = 1 + \frac{3}{2}\left(\frac{|\Delta P_{i-2}|\theta_{i-1}}{|\Delta P_{i-2}|+|\Delta P_{i-1}|} + \frac{|\Delta P_i|\theta_{i-1}}{|\Delta P_{i-1}|+|\Delta P_i|}\right)

\theta_i = \min\left(\pi - \angle P_{i-1}P_iP_{i+1}, \frac{\pi}{2}\right),\ |\Delta P_{-1}| = |\Delta P_n| = 0

弦长修正系数 K_i ≥1。从上述公式可知，与前后相邻弦长 |ΔP_{i-2}| 和 |ΔP_i| 相比，若 |ΔP_{i-1}| 越小，且与前后相邻弦边的夹角的外角