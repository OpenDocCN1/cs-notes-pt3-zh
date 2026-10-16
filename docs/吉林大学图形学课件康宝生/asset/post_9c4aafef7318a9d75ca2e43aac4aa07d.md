
## (2) 沿 y 轴方向的错切变换

沿 y 轴方向的错切变换矩阵为：

⎡ 1  0  0 ⎤
⎢ r₂₁ 1  0 ⎥
⎣ 0  0  1 ⎦

其变换结果为：

⎡ x* ⎤   ⎡ 1  0  0 ⎤ ⎡ x ⎤   ⎡   x   ⎤
⎢ y* ⎥ = ⎢ r₂₁ 1  0 ⎥ · ⎢ y ⎥ = ⎢ y + r₂₁ x ⎥
⎣ 1  ⎦   ⎣ 0  0  1 ⎦ ⎣ 1 ⎦   ⎣   1   ⎦

即： x* = x； y* = y + r₂₁ x。

## 4. 旋转变换

在二维平面内，如不加说明，则所说旋转变换是指图形绕坐标系原点旋转。且逆时针旋转，角度 θ 取正值；顺时针旋转，角度 θ 取负值。旋转变换矩阵为：

```
\begin{bmatrix} \cos\theta & -\sin\theta & 0 \\ \sin\theta & \cos\theta & 0 \\ 0 & 0 & 1 \end{bmatrix}
```

其变换结果为：

```
\begin{bmatrix} x^* \\ y^* \\ 1 \end{bmatrix} = \begin{bmatrix} \cos\theta & -\sin\theta & 0 \\ \sin\theta & \cos\theta & 0 \\ 0 & 0 & 1 \end{bmatrix} \cdot \begin{bmatrix} x \\ y \\ 1 \end{bmatrix} = \begin{bmatrix} x \cdot \cos\theta - y \cdot \sin\theta \\ x \cdot \sin\theta + y \cdot \cos\theta \\ 1 \end{bmatrix}
```

如图所示，由于：

x* = r·cos(α + θ) = r·cos α cos θ − r·sin α sin θ = x cos θ − y sin θ

y* = r·sin(α + θ) = r·sin α cos θ + r·cos α sin θ = x sin θ + y cos θ

由此得到旋转变换矩阵。

![](img/dce279c4fd8230bfee452d9f1db7cf9c_545_0.png)

![](img/dce279c4fd8230bfee452d9f1db7cf9c_545_1.png)

## 5. 平移变换

平移变换矩阵为：

```
[ 1 0 t_x ]
[ 0 1 t_y ]
[ 0 0 1 ]
```

![](img/dce279c4fd8230bfee452d9f1db7cf9c_546_0.png)

其变换结果为：

```
[ x* ]   [ 1 0 t_x ] [ x ]   [ x + t_x ]
[ y* ] = [ 0 1 t_y ]·[ y ] = [ y + t_y ]
[ 1  ]   [ 0 0 1   ] [ 1 ]   [ 1      ]
```

### 5.2.2 二维组合变换

在前面介绍的五种变换都属于基本变换。但实际应用中，大部分图形的变换是不能仅靠单独的基本变换来实现的，而是需要经多次变换才能实现。这种由多个基本变换组合（级联）而成的复杂变换过程称为组合变换。

### 1. 对任意直线的对称变换

前面介绍过五种对称变换，但对称轴都是特殊位置直线。对于对称轴是任意位置直线的对称变换，以上的对称变换矩阵都不能直接应用。

例如，设任意直线的方程为：

$$Ax+By+C=0$$

该直线在 $x$、$y$ 两轴上的截距分别为 $-C/A$ 和 $-C/B$；直线的斜率为 $\tan\alpha=-A/B$。

![](img/dce279c4fd8230bfee452d9f1db7cf9c_548_0.png)

那么，如何实现关于该直线的对称变换呢？

（2）让直线绕坐标系原点旋转 -α 角，使与 x 轴重合。变换矩阵为：

$$T_2=\begin{bmatrix}\cos\alpha&\sin\alpha&0\\-\sin\alpha&\cos\alpha&0\\0&0&1\end{bmatrix}$$

![](img/dce279c4fd8230bfee452d9f1db7cf9c_550_0.png)

![](img/dce279c4fd8230bfee452d9f1db7cf9c_550_1.png)

（3）由于原直线已与 $x$ 轴重合，于是对于直线的对称变换即为对于 $x$ 轴的对称变换。变换矩阵为：

$$T_3=\begin{bmatrix}1&0&0\\0&-1&0\\0&0&1\end{bmatrix}$$

（4）绕原点旋转 $\alpha$ 角，使直线恢复到原倾斜位置。变换矩阵为：

$$T_4=\begin{bmatrix}\cos\alpha&-\sin\alpha&0\\\sin\alpha&\cos\alpha&0\\0&0&1\end{bmatrix}$$

![](img/dce279c4fd8230bfee452d9f1db7cf9c_552_0.png)

![](img/dce279c4fd8230bfee452d9f1db7cf9c_552_1.png)

关于 x 轴的对称变换

旋转

（5）让直线沿 x 轴方向平移 - C/A，使其回到原来位置。

变换矩阵为：

```
T₅ = [[1, 0, -C/A], [0, 1, 0], [0, 0, 1]]
```

综合以上的五步，对任意直线的对称变换过程为：

```
\begin{bmatrix} x^* \\ y^* \\ 1 \end{bmatrix} = T_5 \cdot T_4 \cdot T_3 \cdot T_2 \cdot T_1 \cdot \begin{bmatrix} x \\ y \\ 1 \end{bmatrix} = T \cdot \begin{bmatrix} x \\ y \\ 1 \end{bmatrix}
```

![](img/dce279c4fd8230bfee452d9f1db7cf9c_553_0.png)

其组合变换矩阵：

```
T = T_5 \cdot T_4 \cdot T_3 \cdot T_2 \cdot T_1 = \begin{bmatrix} \cos 2\alpha & \sin 2\alpha & C / A (\cos 2\alpha -1) \\ \sin 2\alpha & -\cos 2\alpha & C / A \sin 2\alpha \\ 0 & 0 & 1 \end{bmatrix}
```

### 2. 绕任意点的旋转变换

绕坐标原点以外的任意点 P(x, y) 的旋转如图所示。

![](img/dce279c4fd8230bfee452d9f1db7cf9c_554_0.png)

前面介绍的旋转是以坐标系原点为旋转中心的，现在的旋转中心 P 不在原点，所以不能简单地套用上面的旋转变换矩阵，我们可以通过以下几个基本变换来完成。

（3）复原。使旋转中心从坐标系原点平移到原来的位置 (x, y)，变换矩阵为：

T₃ = ⎡1 0 x⎤
    ⎢0 1 y⎥
    ⎣0 0 1⎦

所以，绕任意点 P(x, y) 的旋转过程为：

⎡x*⎤   ⎡x⎤
⎢y*⎥ = T₃ · T₂ · T₁ · ⎢y⎥ = T · ⎢y⎥
⎣1 ⎦   ⎣1⎦           ⎣1⎦

即组合变换矩阵为：

T = T₃ · T₂ · T₁ = \begin{bmatrix} \cos \theta & -\sin \theta & x(1-\cos \theta)+y\sin \theta \\ \sin \theta & \cos \theta & -x\sin \theta + y(1-\cos \theta) \\ 0 & 0 & 1 \end{bmatrix}

从上述两个例子的解题过程可以看到，对于一般条件下的图形变换，解决问题的思路可以分为三步：

- Step1. 分析变换的性质；
- Step2. 分解改变成可用基本变换实现；
- Step3. 恢复原状态。

### 3. 级联顺序对组合变换的影响

由于矩阵的乘法运算不适用交换律，即两个矩阵的左乘和右乘，其结果是不相等的。所以在矩阵的乘法中，由于先后次序不同，得到的结果是不同的。这就是说，用基本变换的级联来实现图形的组合变换时，矩阵级联的顺序不同，则所得到的最终结果图形也不同。下面我们举例说明矩阵级联的顺序对变换结果图形的影响。

给定以平移变换和一旋转变换：

T₁ = [[1, 0, c₁], [0, 1, c₂], [0, 0, 1]],  T₂ = [[cos α, -sin α, 0], [sin α, cos α, 0], [0, 0, 1]]

先进行平移变换，然后再进行旋转变换，则最后的结果为：

T = T₂ · T₁ = [[cos α, -sin α, c₁ cos α - c₂ sin α], [sin α, cos α, c₁ sin α + c₂ cos α], [0, 0, 1]]

反过来，若先进行旋转变换，然后再进行平移变换，则最后的结果为：
