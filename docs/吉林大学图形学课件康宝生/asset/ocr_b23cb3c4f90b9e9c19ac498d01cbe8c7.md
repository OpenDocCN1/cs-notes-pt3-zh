# 4.7.3 圆锥曲线的 NURBS 表示

二次 NURBS 曲线

$$R_2(u)=\frac{(1-u)^2\omega_0\boldsymbol{d}_0+2u(1-u)\omega_1\boldsymbol{d}_1+u^2\omega_2\boldsymbol{d}_2}{(1-u)^2\omega_0+2u(1-u)\omega_1+u^2\omega_2},\quad 0\le u\le 1$$

是一条圆锥曲线，其形状分类如下：

$$\frac{\omega_0\omega_2}{\omega_1^2}\begin{cases}=0, & \text{一对直线段 }\overrightarrow{d_0d_1}\text{ 与 }\overrightarrow{d_1d_2}\\\in(0,1), & \text{双曲线}\\=1, & \text{抛物线}\\\in(1,+\infty), & \text{椭圆}\\\to+\infty, & \text{连接 }d_0\text{ 与 }d_2\text{ 的直线段}\end{cases}$$