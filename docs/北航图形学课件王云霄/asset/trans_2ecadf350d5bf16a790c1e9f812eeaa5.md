

![](img/4628856fffb4db710a3ae3a299935a63_149_0.png)

窗口到视区

用户坐标系

窗口

屏幕

视口

## 窗口与视见区的差别

窗口是在用户坐标系中确定的，用来指出需要显示的图形范围；视见区是在设备坐标系中确定的，用来指出实际显示的图形位于显示屏幕的哪一部分。

视见区用于显示窗口中的图形。

## 视见变换的实现

视见变换就是把用户坐标系窗口中指定的图形转换到设备坐标系视区中显示的过程。

窗口：左下角点（wxl, wyb），右上角点（wxh, wyh）

视区：左下角点（vxl, vyl），右上角点（vxh, vyh）

- 1. \(\frac{x_w - wxl}{wxh - wxl} = \frac{x_v - vxl}{vxh - vxl}\)

  \(x_v = vxl + (x_w - wxl) \cdot \frac{vxh - vxl}{wxh - wxl}\)

  同理 \(y_v = vyl + (y_w - wyb) \cdot \frac{vyh - vyl}{wyh - wyb}\)

\[
H = T_1(-wxl, -wyb) \cdot S(s_x, s_y) \cdot T_2(vxl, vyl)
\]

\[
= \begin{bmatrix}
1 & 0 & 0 \\
0 & 1 & 0 \\
-wxl & -wyb & 1
\end{bmatrix}
\begin{bmatrix}
\frac{vxh-vxl}{wxh-wxl} & 0 & 0 \\
0 & \frac{vyh-vyl}{wyh-wyb} & 0 \\
0 & 0 & 1
\end{bmatrix}
\begin{bmatrix}
1 & 0 & 0 \\
0 & 1 & 0 \\
vxl & vyl & 1
\end{bmatrix}
\]

\[
= \begin{bmatrix}
\frac{vxh-vxl}{wxh-wxl} & 0 & 0 \\
0 & \frac{vyh-vyl}{wyh-wyb} & 0 \\
vxl - wxl \cdot \frac{vxh-vxl}{wxh-wxl} & vyl - wyb \cdot \frac{vyh-vyl}{wyh-wyb} & 1
\end{bmatrix}
\]

\[
s_x = \frac{vxh-vxl}{wxh-wxl}, \quad s_y = \frac{vyh-vyl}{wyh-wyb}
\]

设窗口内图形上一点的坐标为 \((x, y)\)，该点在视见区中的显示坐标为 \((x', y')\)，利用视见变换矩阵可得如下计算公式：

\[
x' = vxl + (x - wxl)\frac{vxh - vxl}{wxh - wxl}
\]

\[
y' = vyl + (y - wyb)\frac{vyh - vyl}{wyh - wyb}
\]

## 第四节 三维图形变换

\[
P = [x \quad y \quad z \quad 1], \quad P' = [x' \quad y' \quad z' \quad 1]
\]

### 1. 平移变换

\[
P' = [x' \quad y' \quad z' \quad 1] = [x \quad y \quad z \quad 1]
\begin{bmatrix}
1 & 0 & 0 & 0 \\
0 & 1 & 0 & 0 \\
0 & 0 & 1 & 0 \\
D_x & D_y & D_z & 1
\end{bmatrix}
\]

\[
= P \cdot T(D_x, D_y, D_z)
\]

### 2. 比例变换

\[
P' = [x' \ y' \ z' \ 1] = [x \ y \ z \ 1]
\begin{bmatrix}
S_x & 0 & 0 & 0 \\
0 & S_y & 0 & 0 \\
0 & 0 & S_z & 0 \\
0 & 0 & 0 & 1
\end{bmatrix}
\]

\[
= P \cdot S(S_x, S_y, S_z)
\]

图 3.10 以坐标原点为参考点的三维比例变换

![](img/4628856fffb4db710a3ae3a299935a63_159_0.png)

(a)

(b) 平移至原点

(c) 比例变换

(d) 平移回 P 点

图 3.11 以任意点 P 为参考点的三维比例变换过程

### 3. 旋转变换

![](img/4628856fffb4db710a3ae3a299935a63_160_0.png)

图 3.12 绕三根坐标轴旋转的正方向

#### ① 绕 Z 轴旋转

\[
x' = x \cos\theta - y \sin\theta
\]

\[
y' = x \sin\theta + y \cos\theta
\]

\[
z' = z
\]

\[
P' = [x' \ y' \ z' \ 1] = [x \ y \ z \ 1]
\begin{bmatrix}
\cos\theta & \sin\theta & 0 & 0 \\
-\sin\theta & \cos\theta & 0 & 0 \\
0 & 0 & 1 & 0 \\
0 & 0 & 0 & 1
\end{bmatrix}
\]

\[
= P \cdot R_z(\theta)
\]

#### ③ 绕 Y 轴旋转

\[
x' = x \cos\theta + z \sin\theta
\]

\[
y' = y
\]

\[
z' = -x \sin\theta + z \cos\theta
\]

\[
P' = [x' \ y' \ z' \ 1] = [x \ y \ z \ 1]
\begin{bmatrix}
\cos\theta & 0 & -\sin\theta & 0 \\
0 & 1 & 0 & 0 \\
\sin\theta & 0 & \cos\theta & 0 \\
0 & 0 & 0 & 1
\end{bmatrix}
\]

\[
= P \cdot R_y(\theta)
\]

### 4. 对称变换

- （1）相对于 xy 平面的对称变换，z=0 平面

\[
\begin{bmatrix}
1 & 0 & 0 & 0 \\
0 & 1 & 0 & 0 \\
0 & 0 & -1 & 0 \\
0 & 0 & 0 & 1
\end{bmatrix}
\]

- （2）相对于 xz 平面的对称变换，y=0 平面

\[
\begin{bmatrix}
1 & 0 & 0 & 0 \\
0 & -1 & 0 & 0 \\
0 & 0 & 1 & 0 \\
0 & 0 & 0 & 1
\end{bmatrix}
\]

- （3）相对于 yz 平面的对称变换，x=0 平面

\[
\begin{bmatrix}
-1 & 0 & 0 & 0 \\
0 & 1 & 0 & 0 \\
0 & 0 & 1 & 0 \\
0 & 0 & 0 & 1
\end{bmatrix}
\]

- （4）相对于空间任一平面做对称变换
  - 1）将此平面变换为与某一坐标面重合
  - 2）做相对于该坐标面的对称变换
  - 3）将平面反变换回原位置

### 5. 错切变换

\[
\begin{bmatrix}
1 & b & c & 0 \\
d & 1 & f & 0 \\
g & h & 1 & 0 \\
0 & 0 & 0 & 1
\end{bmatrix}
\]

\[
x' = x + d y + g z, \quad d, g \neq 0 \text{（关于 x 轴方向有错切）}
\]

\[
y' = y + b x + h z, \quad b, h \neq 0 \text{（关于 y 轴方向有错切）}
\]

\[
z' = z + c x + f y, \quad c, f \neq 0 \text{（关于 z 轴方向有错切）}
\]

### 三维图形变换

\[
\begin{bmatrix}
a & b & c & p \\
d & e & f & q \\
g & h & i & r \\
l & m & n & s
\end{bmatrix}
\]

\[
\begin{bmatrix}
a & b & c \\
d & e & f \\
g & h & i
\end{bmatrix}
\]

旋转、比例、对称、错切变换

\[
\begin{bmatrix}
l & m & n
\end{bmatrix}
\]

平移变换

\[
\begin{bmatrix}
p \\ q \\ r
\end{bmatrix}
\]

投影变换

\[
[s]
\]

整体比例变换

例：设三维空间中有一条任意直线，它由直线上一点 Q 和沿直线方向的单位方向向量 n 确定。  
Q 点坐标为 \((x_0, y_0, z_0)\)  
直线向量 \(\mathbf{n} = [n_1 \ n_2 \ n_3]\)，\(|\mathbf{n}| = \sqrt{n_1^2 + n_2^2 + n_3^2} = 1\)  
求绕这条直线旋转 \(\theta\) 角的旋转变换矩阵。

![](img/4628856fffb4db710a3ae3a299935a63_169_0.png)

图 3.14 以空间任意直线为轴的三维旋转变换

\[
T(-x_0, -y_0, -z_0) \cdot R(\theta) \cdot T(x_0, y_0, z_0)
\]

过坐标原点的任意直线为旋转轴的旋转变换可分为五步实现：

- (1) 做绕 X 轴旋转 α 角的变换，使旋转轴落在 Y=0 上。
- (2) 做绕 Y 轴旋转 β 角的变换，使旋转轴与 Z 轴重合。
- (3) 做绕 Z 轴旋转 θ 角的旋转变换。
- (4) 做第 2 步的逆变换，即做绕 Y 轴旋转 -β 角的变换。
- (5) 做第 1 步的逆变换，即做绕 X 轴旋转 -α 角的变换。

![](img/4628856fffb4db710a3ae3a299935a63_171_0.png)

![](img/4628856fffb4db710a3ae3a299935a63_171_1.png)

图 3.15 绕 X 轴旋转 \(\alpha\) 角（右面是在 X=0 平面上的投影）

\[
v = \sqrt{n_2^2 + n_3^2}
\]

\[
\cos\alpha = \frac{n_3}{v}, \quad \sin\alpha = \frac{n_2}{v}
\]

