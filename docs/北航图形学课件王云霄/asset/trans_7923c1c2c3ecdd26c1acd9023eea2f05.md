

\[
H=T(-1,-1,-1)\cdot R_z(45^\circ)\cdot R_x(-135^\circ)\cdot R_z(180^\circ)
=
\begin{bmatrix}
-\frac{\sqrt{2}}{2} & \frac{1}{2} & -\frac{1}{2} & 0 \\
\frac{\sqrt{2}}{2} & \frac{1}{2} & -\frac{1}{2} & 0 \\
0 & -\frac{\sqrt{2}}{2} & -\frac{\sqrt{2}}{2} & 0 \\
0 & \frac{\sqrt{2}}{2}-1 & \frac{\sqrt{2}}{2}+1 & 1
\end{bmatrix}
\]

## 解法二：

- ① \(T(-1,-1,-1)\)
- ② \(R_z(-135^\circ)\)

  \[
  \begin{bmatrix}
  0 & -\sqrt{2} & \sqrt{2} & 1 \\
  0 & -2\sqrt{2} & 2 & 1
  \end{bmatrix}
  \]

- ③ \(R_x(135^\circ)\)

  \[
  \begin{bmatrix}
  0 & 0 & -2 & 1 \\
  0 & 2-\sqrt{2} & -2-\sqrt{2} & 1
  \end{bmatrix}
  \]

## 解法三：

- ① \(T(-1,-1,-1)\)
- ② \(R_x(\alpha)\)，\(\sin\alpha=\frac{1}{\sqrt{3}}\)，\(\cos\alpha=\frac{\sqrt{2}}{\sqrt{3}}\)
- ③ \(R_y(\beta)\)，\(\sin\beta=\frac{1}{2}\)，\(\cos\beta=-\frac{\sqrt{3}}{2}\)
- ④ \(R_z(\theta)\)，\(\sin\theta=-\frac{1}{\sqrt{3}}\)，\(\cos\theta=\frac{\sqrt{2}}{\sqrt{3}}\)

## 解法四：

\(H=T(-1,-1,-1)\cdot R_z(-45^\circ)\cdot R_y(135^\circ)\cdot R_z(-90^\circ)\)

\[
\begin{bmatrix}
0 & 0 & 0\\
1 & 1 & \sqrt{2}\\
2 & 2 & 2
\end{bmatrix}
\rightarrow
\begin{bmatrix}
0 & 0 & 0\\
\sqrt{2} & 0 & \sqrt{2}\\
2\sqrt{2} & 0 & 2
\end{bmatrix}
\rightarrow
\begin{bmatrix}
0 & 0 & 0\\
0 & 0 & -2\\
-2 & 0 & -2-\sqrt{2}
\end{bmatrix}
\rightarrow
\begin{bmatrix}
0 & 0 & 0\\
0 & 0 & -2\\
0 & 2-\sqrt{2} & -2-\sqrt{2}
\end{bmatrix}
\]

## 19题：平面方程 \(Ax+By+Cz+D=0\)

法向：\((A,B,C)\)。

a. 设 \(D\ne0\)，又因为 \(A,B,C\) 不能全为0，设 \(A\ne0\)，则 \((-D/A,0,0)\) 是平面上的点。

\(T(D/A,0,0)\)

b. 做旋转变换使平面的法向量与 \(z\) 轴重合。

\(R_x(\alpha)\)，令 \(v=\sqrt{B^2+C^2}\)，\(\cos\alpha=C/v\)，\(\sin\alpha=B/v\)

\(R_y(\beta)\)，令 \(d=\sqrt{A^2+B^2+C^2}\)，\(\cos\beta=v/d\)，\(\sin\beta=-A/d\)

\[
H=T(D/A,0,0)\cdot R_x(\alpha)\cdot R_y(\beta)
=
\begin{bmatrix}
\frac{v}{d} & 0 & -\frac{A}{d} & 0 \\
\frac{AB}{vd} & \frac{C}{v} & \frac{B}{d} & 0 \\
\frac{AC}{vd} & -\frac{B}{v} & \frac{C}{d} & 0 \\
\frac{Av}{Bd} & 0 & -\frac{A^2}{Bd} & 1
\end{bmatrix}
\]

## 22题

设定任一点 \((x,y,z)\) 投影后的点为 \((x_p,y_p,z_p)\)，则

\[
(x_p-x,\ y_p-y,\ z_p-z)=k(l,m,n)
\]

\[
x_p=x+kl,\quad y_p=y+km,\quad z_p=z+kn
\]

因为投影平面为 \(z=0\) 平面，

\[
z+kn=0,\quad k=-z/n
\]

\[
x_p=x-lz/n,\quad y_p=y-mz/n
\]

变换矩阵为

\[
\begin{bmatrix}
1 & 0 & 0 & 0 \\
0 & 1 & 0 & 0 \\
-\frac{l}{n} & -\frac{m}{n} & 0 & 0 \\
0 & 0 & 0 & 1
\end{bmatrix}
\]

- ③ 做平行投影（投影平面为 \(Z=0\) 平面，方向为 \(Z\) 轴方向）

  \[
  \begin{bmatrix}
  1 & 0 & 0 & 0\\
  0 & 1 & 0 & 0\\
  0 & 0 & 0 & 0\\
  0 & 0 & 0 & 1
  \end{bmatrix}
  \]

- ④ 做②的逆变换
- ⑤ 做①的逆变换

\[
H=R_y(-45^\circ)\cdot R_x(\beta)\cdot M\cdot R_x(-\beta)\cdot R_y(45^\circ)
\]

## 第一节 曲线和曲面表示的基础知识

### 1. 显式、隐式和参数表示

① 显式：\(y=f(x)\)

不能表示封闭曲线或多值曲线（圆）。

② 隐式：\(f(x,y)=0\)，\(f(x,y,z)=0\)

球面。

### 显式、隐式表示的缺点

- （1）与坐标轴相关的，不便于坐标变换；
- （2）无法解决斜率为无穷大的情况；
- （3）对于空间复杂曲线曲面很难表示；
- （4）不便于计算和编程。

### ③ 参数表示（解决上述问题）

空间曲线：

\[
x=x(t),\quad y=y(t),\quad z=z(t)
\]

矢量表示是：

\[
P(t)=[x(t)\quad y(t)\quad z(t)]
\]

### 空间直线段

已知 \(P_1(x_1,y_1,z_1)\)，\(P_2(x_2,y_2,z_2)\)。

\[
x=x_1+(x_2-x_1)t,\quad y=y_1+(y_2-y_1)t,\quad z=z_1+(z_2-z_1)t,\quad 0\le t\le1
\]

\(P(t)\) 代表曲线上的一点：

\[
P(t)=P_1+(P_2-P_1)t=(1-t)P_1+tP_2
\]

\[
P'(t)=[x'(t)\quad y'(t)\quad z'(t)]=[x_2-x_1\quad y_2-y_1\quad z_2-z_1]
\]

### （2）抛物线插值（二次插值）

设已知 \(f(x)\) 在三个互异点 \(x_1,x_2,x_3\) 的函数值为 \(y_1,y_2,y_3\)，要求构造函数 \(\varphi(x)=ax^2+bx+c\)，\(\varphi(x)\) 在节点 \(x_i\) 处有

\[
\varphi(x_i)=f(x_i)
\]

![](img/4628856fffb4db710a3ae3a299935a63_268_0.png)

### 常用方法 最小二乘法

假设已知一组型值点 \((x_i,y_i)\)，\(i=1,2,\dots,n\)，要求构造一个 \(m\)（\(m<n-1\)）次多项式函数 \(y=F(x)\) 逼近这些型值点。

偏差的平方和最小：

\[
\varphi=\sum_{k=1}^{n}\left(F(x_k)-y_k\right)^2
\]

或加权平方和最小：

\[
\varphi=\sum_{k=1}^{n}d_k\left(F(x_k)-y_k\right)^2
\]

令 \(F(x)\) 为一个 \(m\) 次多项式：

\[
F(x)=\sum_{j=0}^{m}a_jx^j
\]

最小二乘法就是定出 \(a_i\) 使偏差平方和最小。

解四个方程，求得参数：

\[
a_0=P(0),\quad a_1=P'(0)
\]

\[
a_2=-3P(0)+3P(1)-2P'(0)-P'(1)
\]

\[
a_3=2P(0)-2P(1)+P'(0)+P'(1)
\]

令

\[
P_0=P(0),\quad P_1=P(1),\quad P_0'=P'(0),\quad P_1'=P'(1)
\]

\[
P(t)=a_3t^3+a_2t^2+a_1t+a_0
\]

\[
P(t)=(2t^3-3t^2+1)P_0+(-2t^3+3t^2)P_1+(t^3-2t^2+t)P_0'+(t^3-t^2)P_1'
\]

参数曲线的几何形式：

\[
P(t)=F_1P_0+F_2P_1+F_3P_0'+F_4P_1'
\]

- **参数连续性**：一个函数在某一点 \(x_0\) 处具有相等的直到 \(k\) 阶的左右导数，称它在 \(x_0\) 处是 \(k\) 次连续可微的，或称它在 \(x_0\) 处是 \(k\) 阶连续的，记作 \(C^k\)。几何上 \(C^0\)、\(C^1\)、\(C^2\) 依次表示该函数的图形、切线方向、曲率是连续的。参数曲线的可微性称为参数曲线的连续性。

- **几何连续性**：两曲线段的相应的弧长参数化在公共连接点处具有 \(C^k\) 连续性，则称它们在该点处具有 \(k\) 阶几何连续性，记作 \(G^k\)。零阶几何连续 \(G^0\) 与零阶参数连续 \(C^0\) 是一致的。一阶几何连续 \(G^1\) 指一阶导数在两个相邻曲线段的交点处成比例，即方向相同，大小不同。二阶几何连续 \(G^2\) 指两个曲线段在交点处其一阶和二阶导数均成比例。

