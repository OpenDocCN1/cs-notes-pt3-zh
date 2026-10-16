$d_{i+1}=2F(x_i+2,y_i+1+1/2)=2a(x_i+2)+2b(y_i+1)+b+2c$

$=d_i+2a+2b$

由此，得到计算判定函数 $d_i$ 的递推公式：

$d_{i+1}=\begin{cases} d_i+2dy, & d_i\leq 0 \\ d_i+2dy-2dx, & d_i>0 \end{cases}$

因为直线上的第一个像素点就是直线的起点 $(x_s,y_s)$，所以判定函数 $d_i$ 的初值为：

$d_0=2a(x_s+1)+2by_s+b+2c=2dy-dx$