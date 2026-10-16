这四个不等式可以表示为

$$uP_i \le Q_i,\quad i = L,\ R,\ B,\ T$$

其中，$P_i, Q_i$定义如下：

$$
\begin{cases}
P_L = -\Delta x, & Q_L = x_0 - x_L \\
P_R = \Delta x, & Q_R = x_R - x_0 \\
P_B = -\Delta y, & Q_B = y_0 - y_B \\
P_T = \Delta y, & Q_T = y_T - y_0
\end{cases}
$$

任何平行裁剪边界之一的直线满足条件$P_i = 0$，若还满足$Q_i < 0$，则线段完全在边界外，舍弃该线段。若$Q_i \ge 0$，则线段平行于裁剪边界并在窗口内，需用另外一组边界进行检查。