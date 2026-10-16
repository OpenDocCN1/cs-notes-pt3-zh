引进递推表示的中间参量：

$q_i = \frac{-\mu_i}{2 + \lambda_i q_{i-1}},\quad u_i = \frac{C_i - \lambda_i u_{i-1}}{2 + \lambda_i q_{i-1}},\ i = 0,\ 1,\ \cdots,\ m$

并约定 $q_{-1}=0$, $u_{-1}=0$, 则方程组解的递推表示是：

$egin{cases} P'_m = u_m \ P'_i = q_i P'_{i+1} + u_i,\ i = m-1,\ m-2,\ \cdots,1,0 \end{cases}$

求解插值三次参数样条曲线的步骤，可归纳如下：

+   （1）根据具体问题的要求，确定适当的边界条件；
+   （2）用“追赶法”解方程组，求出节点 $t_i$ 处的一阶导数：
+   
+   $P'_i,\ i = 0,1,\cdots,m$