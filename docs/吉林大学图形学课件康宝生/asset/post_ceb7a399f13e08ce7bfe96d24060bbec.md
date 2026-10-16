
Step2. 沿 x̄ 方向和 ȳ 方向做错切变换，把经过 TR 变换后的棱台变成正棱台，该变换矩阵为：

\[
\overline{SH} = \begin{bmatrix}
1 & 0 & -(\bar{x}_1'' + \bar{x}_3'' - 2\bar{x}_c)/(2(\bar{z}_b - \bar{z}_c)) & 0 \\
0 & 1 & -(\bar{y}_1'' + \bar{y}_2'' - 2\bar{y}_c)/(2(\bar{z}_b - \bar{z}_c)) & 0 \\
0 & 0 & 1 & 0 \\
0 & 0 & 0 & 1
\end{bmatrix}
\]

Step3. 做缩放变换，使正棱台变为规范化观察体，其变换矩阵是：

\[
\bar{S} = \begin{bmatrix}
(\bar{x}_3'' - \bar{x}_2'')^{-1} & 0 & 0 & 0 \\
0 & (\bar{y}_2'' - \bar{y}_1'')^{-1} & 0 & 0 \\
0 & 0 & (\bar{z}_b - \bar{z}_c)^{-1} & 0 \\
0 & 0 & 0 & 1
\end{bmatrix}
\]

那么，从观察坐标系 oxyz 到规范化坐标系 oᵥxᵥyᵥzᵥ 的变换为

\[
(x_v, y_v, z_v, 1)^T = \bar{S} \cdot \overline{SH} \cdot \overline{TR} \cdot (\bar{x}, \bar{y}, \bar{z}, 1)^T
\]

同样，当透视投影的三维观察体在世界坐标系中指定时，将上式和前面的坐标变换公式合并，亦可得到从世界坐标系到规范化坐标系 oᵥxᵥyᵥzᵥ 的变换公式。

## 本章作业

- 1. 建立图形绕点 (x_c, y_c) 旋转 θ 角度的旋转变换公式。
- 2. 设投影中心为 (0, 0, 8), 投影平面为 z = 1, 求在该投影变换下, 点的变换公式。
- 3. 证明三维几何变换矩阵的乘积对以下运算顺序是可交换的：
  - (a) 任意两个连续平移变换；
  - (b) 任意两个连续的缩放变换。
- 4. 投影变换可分为几类？

## 第七章 参数曲面

![](img/dce279c4fd8230bfee452d9f1db7cf9c_642_0.png)

### 7.1 参数曲面的基本概念

和曲线一样，曲面也有显式表示、隐式表示和参数表示，计算机图形学中最常用的是参数表示。通常采用矩形域作为曲面的参数域。

一张定义在矩形参数域上的参数曲面可以表示为：

\[
\begin{aligned}
x &= x(u, v) \\
y &= y(u, v), \quad (u, v) \in [0, 1] \times [0, 1] \\
z &= z(u, v)
\end{aligned}
\]

记为 \(P(u, v) = (x(u, v), y(u, v), z(u, v))\)，\((u, v)\) 称为参数。

参数曲面中常见的基本概念如下：

- 1. 曲面上的点 将参数 \(u_0, v_0\) 代入参数方程，可得曲面上的点 \(P(u_0, v_0)\)。

- 2. 曲面上一点的切向量（切矢） 对给定的参数 \(u_0, v_0\)，曲面上的点 \(P(u_0, v_0)\) 处的 u 向切矢和 v 向切矢分别为：

\[
\left.\frac{\partial P(u,v)}{\partial u}\right|_{u=u_0, v=v_0}
\qquad
\left.\frac{\partial P(u,v)}{\partial v}\right|_{u=u_0, v=v_0}
\]

![](img/dce279c4fd8230bfee452d9f1db7cf9c_644_0.png)

- 3. 曲面上一点的法向量（法矢） 对给定的参数 \(u_0, v_0\)，曲面上的点 \(P(u_0, v_0)\) 处的法向量为：

\[
N(u_0, v_0) = \left.\frac{\partial P(u,v)}{\partial u}\right|_{u=u_0, v=v_0} \times \left.\frac{\partial P(u,v)}{\partial v}\right|_{u=u_0, v=v_0}
\]

- 4. 角点 将参数 \(u, v = 0\) 或 1 代入曲面上的参数方程 \(P(u, v)\)，得到曲面的 4 个角点为：\(P(0, 0), P(0, 1), P(1, 0)\) 和 \(P(1, 1)\)，简记为 \(P_{00}, P_{01}, P_{10}, P_{11}\)。

- 5. 边界线 将参数 \(u = 0, 1\) 或 \(v = 0, 1\) 代入曲面上的参数方程 \(P(u, v)\)，得到曲面的 4 条边界线为：\(P(u, 0), P(u, 1), P(0, v)\) 和 \(P(1, v)\)，简记为 \(P_{u0}, P_{u1}, P_{0v}, P_{1v}\)。

### 7.2 二次曲面和超二次曲面

二次曲面是一类常用的物体，由二次方程描述，包括球面、椭球面、环面、抛物面和双曲面。二次曲面，尤其是球面和椭球面，是最基本的图形物体，经常作为图元用在图形包中，由此可以构造更复杂的物体。

#### 7.2.1 球面

在笛卡儿坐标系中，球心在原点，半径为 r 的球面定义为满足下列方程的点集 (x, y, z)：

\[
x^2 + y^2 + z^2 = r^2
\]

我们也可以用参数形式来描述球面，使用球面坐标可得球面的参数方程：

\[
\begin{cases}
x = r \cos\varphi \cos\theta \\
y = r \cos\varphi \sin\theta, \quad 0 \le \varphi \le \pi, \ 0 \le \theta \le 2\pi \\
z = r \sin\varphi
\end{cases}
\]

#### 7.2.2 椭球面

椭球面可以看成是球面的扩展，它的三条相互垂直的主半轴有不同的长度。椭球面中心在原点的笛卡儿表示式为：

\[
\left(\frac{x}{r_x}\right)^2 + \left(\frac{y}{r_y}\right)^2 + \left(\frac{z}{r_z}\right)^2 = 1
\]

相应地，椭球面的参数方程为：

\[
\begin{cases}
x = r_x \cos\varphi \cos\theta \\
y = r_y \cos\varphi \sin\theta, \quad 0 \le \varphi \le \pi, \ 0 \le \theta \le 2\pi \\
z = r_z \sin\varphi
\end{cases}
\]

#### 7.2.3 环面

环面是轮胎形状物体，将圆或其他二次曲线绕指定轴旋转而成。在笛卡儿坐标系中，环面的方程是：

\[
\left[ r - \sqrt{\left(\frac{x}{r_x}\right)^2 + \left(\frac{y}{r_y}\right)^2} \right]^2 + \left(\frac{z}{r_z}\right)^2 = 1
\]

其中，r 是给定的偏移量。环面的参数方程类似于椭球面，其表示式如下：

\[
\begin{cases}
x = r_x (r + \cos\varphi) \cos\theta \\
y = r_y (r + \cos\varphi) \sin\theta, \quad -\pi \le \varphi \le \pi, \ -\pi \le \theta \le \pi \\
z = r_z \sin\varphi
\end{cases}
\]

#### 7.2.4 超二次曲面

超二次曲面（super quadrics）由二次方程添加参数而成，对调整物体形状增加了方便。增加的参数数目等同于物体的维数：曲线一个参数，曲面二个参数。

#### 超椭圆

在椭圆相应的方程中，允许 x 和 y 的指数是变量，这样可以得到超椭圆的笛卡儿表示式。笛卡儿坐标系下，超椭圆方程的表示形式之一是：

\[
\left(\frac{x}{r_x}\right)^{2/s} + \left(\frac{y}{r_y}\right)^{2/s} = 1
\]

其中，参数 s 是任何实数。当 s=1 时，为一般椭圆的表示式。超椭圆的参数方程是：

\[
\begin{cases}
x = r_x \cos^s\theta \\
y = r_y \sin^s\theta
\end{cases}, \quad 0 \le \theta \le 2\pi
\]

#### 超椭球面

超椭球面的表示式是由椭球面方程增加二个指数参数而得：

\[
\left[\left(\frac{x}{r_x}\right)^{2/s_2} + \left(\frac{y}{r_y}\right)^{2/s_2}\right]^{s_2/s_1} + \left(\frac{z}{r_z}\right)^{2/s_1} = 1
\]

当 \(s_1 = s_2 = 1\) 时，得到一般的椭球面。超椭球面的参数方程是：

\[
\begin{cases}
x = r_x \cos^{s_1}\varphi \cos^{s_2}\theta \\
y = r_y \cos^{s_1}\varphi \sin^{s_2}\theta, \quad -\frac{\pi}{2} \le \varphi \le \frac{\pi}{2}, \ -\pi \le \theta \le \pi \\
z = r_z \sin^{s_1}\varphi
\end{cases}
\]

### 7.3 柔性物体

有些物体不具有固定形状，当处于运动状态或接近其他物体时其表面特征会发生变化，如分子结构、水珠、带状物体、人体肌肉等。这些物体具有“柔性”，称之为柔性物体 (blobby objects)，因为这些物体具有一定程度的流动性。

例如，分子形状在独立存在时可用球面描述，但当分子接近其他分子时，其形状发生改变。电子云形状的变形便是由于两个分子间发生“结合”而产生延伸、分裂和收缩效果。这些特性不能简单地用球面或椭球面来描述。

目前已开发了几种用分布函数来表示柔性物体的建模方法，其一是用 Gauss 密度函数的组合来对物体建模，表面函数定义如下：

\[
f(x,y,z)=\sum_k b_k e^{-a_k r_k^2}-T=0
\]

其中，\(r_k=\sqrt{x_k^2+y_k^2+z_k^2}\)，\(T\) 是某个特定临界值，参数 \(a_k\)、\(b_k\) 用来调整单个柔性物体。

另一些用来生成柔性物体的方法是使用在几个区间取 0 值而不是指数形式的密度函数。元球（metaball）模型将柔性物体看成几个二次密度函数的集合：
