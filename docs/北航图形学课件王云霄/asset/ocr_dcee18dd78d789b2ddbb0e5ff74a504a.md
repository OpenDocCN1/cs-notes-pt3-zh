为了完整地写出这个插值多项式，可以在区间[$t_i$, $t_{i+1}$]中引入如下一些基本函数：

$a_{0,0}(t)=\begin{cases} g_{0,0}(t), & t_0\le t\le t_1 \\ 0, & t_1\le t\le t_n \end{cases}$

$a_{i,0}(t)=\begin{cases} g_{i-1,1}(t), & t_{i-1}\le t\le t_i \\ g_{i,0}(t), & t_i\le t\le t_{i+1} \\ 0, & \text{其它} \end{cases}\quad i=1,2,\cdots n-1$