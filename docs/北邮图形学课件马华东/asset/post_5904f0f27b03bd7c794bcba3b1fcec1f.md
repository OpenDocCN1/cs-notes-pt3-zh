
## 多边形属性

通常多边形用实心模式填充，但也可以利用下面命令指定某种点画模式（图案）来填充：

```
void glPolygonStipple(const GLubyte *mask);
```

该函数指定多边形点画模式。`mask` 指定32×32点画模式（位图）的指针，值为1时绘，值为0时不绘。指定多边形点画模式需要利用 `glEnable(GL_POLYGON_STIPPLE)` 激活。

### 10.3.4 控制多边形绘制

**选择绘制多边形的方式**

利用下面函数可以选择绘制多边形的方式。

```
void glPolygonMode(GLenum face, GLenum mode);
```

`face` 控制多边形的正面和反面的绘图方式，有3种绘制方式：`GL_FRONT_AND_BACK`、`GL_FRONT`、`GL_BACK`。

`mode` 控制绘点、线框或填充多边形，有 `GL_POINT`、`GL_LINE` 和 `GL_FILL`。

**反转多边形面**

在 OpenGL 中，每个多边形被认为是由两个面组成的：正面和反面。

```
glFrontFace(GLenum mode);
```

该函数定义多边形的正面方向：

- `mode = GL_CW`（顺时针方向为正面）
- `mode = GL_CCW`（逆时针方向为正面，缺省值）

**法向量**

利用下面函数设置当前法向量：

```
void glNormal3{bsidf}(TYPE nx, TYPE ny, TYPE nz);
```

`nx, ny, nz` 指定法向量的 x、y 和 z 坐标。法向量的缺省值为 (0, 0, 1)。

利用命令 `glEnable(GL_NORMALIZE)` 激活自动规格化法向量，就会自动规格化 `glNormal*()` 所指定的法向量。

**指定的法向量，绘制多边形**

```
glBegin(GL_POLYGON); // n0, n1, n2, n3, n4 已定义
glNormal3fv(n0);
glVertex2f(0.0, 0.0);
glNormal3fv(n1);
glVertex2f(0.0, 3.0);
glNormal3fv(n2);
glVertex2f(3.0, 3.0);
glNormal3fv(n3);
glVertex2f(4.0, 1.5);
glNormal3fv(n4);
glVertex2f(3.0, 0.0);
glEnd();
```

## 10.4 坐标变换

- 概述
- 常用的变换函数
- 视图造型变换
- 投影变换
- 视口变换

### 10.4.1 概述

OpenGL 的坐标变换的步骤分为如下4步：

1. 第1步 指定视图和造型变换，两者结合称为视图造型变换。WC → VC
2. 第2步 指定投影变换，使对象从视觉坐标变换到裁剪坐标。VC → CC
3. 第3步 通过对坐标值除以 w，执行透视除法，变换到规格化设备坐标。CC → NDC
4. 第4步 通过视口变换将坐标变换到窗口坐标。NDC → WinC

### 10.4.2 常用的变换函数

- 变换和矩阵是相关的。
- `void glMatrixMode(GLenum mode)`
  该函数指定哪一种矩阵为当前矩阵。
  `mode` 为当前矩阵的类型，可以有：
  - `GL_MODELVIEW` —— 后续的操作均在视图造型变换范围内（缺省值）
  - `GL_PROJECTION` —— 后续的操作均在投影变换范围内
  - `GL_TEXTURE` —— 后续的操作在纹理映射范围内
- `void glLoadIdentity(void)`
  该函数设置单位矩阵为当前矩阵。
- `void glMultMatrix{fd}(const TYPE *m)`
  该函数用任意 4×4 矩阵替代当前矩阵，`m` 指定任意矩阵的 16 个元素。
  参数 `m` 为指定矩阵 M，M 由 16 个值的向量 `(m₁, m₂, …, m₁₆)` 组成。

![](img/c00b4e8ccb17d37f1489c44f2791c008_522_0.png)

### 10.4.3 视图造型变换

- 视图造型变换过程就是一个将顶点坐标从世界坐标变换到观察坐标的过程。

- **变换的顺序**
  当执行变换 A 和 B 时，如果按不同顺序执行，结果往往会大不相同。

**造型变换**

- `void glTranslate*(TYPE x, TYPE y, TYPE z);`
  该函数以平移矩阵乘当前矩阵，`x, y, z` 指定沿世界坐标系 x、y、z 轴的平移量。
- `void glRotate*(TYPE angle, TYPE x, TYPE y, TYPE z);`
  该函数以旋转矩阵乘当前矩阵。`angle` 指定旋转的角度；`x, y, z` 指定旋转轴向量的 3 个分量。
- `void glScale*(TYPE x, TYPE y, TYPE z);`
  该函数以缩放矩阵乘当前矩阵，`x, y, z` 指定沿 x、y 和 z 轴的比例因子。

**视图变换**

视图变换改变视点的位置和方向，也就是改变观察坐标系。作视图变换有以下几种方法：

1. 利用一个或几个造型变换命令（即 `glTranslate*()` 和 `glRotate*()`）。
2. 利用实用库函数 `gluLookAt()` 设置观察坐标系。

```
void gluLookAt(GLdouble eyex, GLdouble eyey, GLdouble eyez, GLdouble centerx, GLdouble centery, GLdouble centerz, GLdouble upx, GLdouble upy, GLdouble upz)
```

- `eyex, eyey, eyez` —— 指定视点的位置；
- `centerx, centery, centerz` —— 指定参考点的位置；
- `upx, upy, upz` —— 指定视点向上方向。

### 10.4.4 投影变换

**透视投影**

其取景体积是一个截头锥体，可用 `glFrustum()` 函数定义这个截头锥体：

```
void glFrustum(GLdouble left, GLdouble right, GLdouble bottom, GLdouble top, GLdouble near, GLdouble far);
```

该函数以透视矩阵乘当前矩阵。

- `left, right` 指定左右垂直裁剪面的坐标；
- `bottom, top` 指定底和顶水平裁剪面的坐标；
- `near, far` 指定近和远深度裁剪面的距离。

**正交投影**

其取景体积是一个各面均为矩形的六面体，可用 `glOrtho()` 函数定义这个六面体：

```
void glOrtho(GLdouble left, GLdouble right,
GLdouble bottom, GLdouble top, GLdouble near,
GLdouble far);
```

该函数以正交投影矩阵乘当前矩阵。

### 10.4.5 视口变换

- 视口就是窗口中矩形绘图区。用窗口管理器在屏幕上打开一个窗口时，已经自动地把视口区设为整个窗口的大小。
- 可以用 `glViewport` 命令设定一个较小的绘图区：

```
void glViewport(GLint x, GLint y, GLsizei width, GLsizei height);
```

该函数设置视口的大小。

`x`、`y` 指定视口矩形的左下角坐标（以像素为单位），缺省值为 `(0, 0)`；

`width`、`height` 分别指定视口的宽和高。

## 10.5 光照明模型处理

- OpenGL 光照明模型的基本概念
- 光源定义
- 光照模型
- 材质属性

### 10.5.1 OpenGL 光照模型的基本概念

- 光线由4个部分构成：发射光、环境光、漫反射光、镜面反射光，这4个成分单独计算，然后再累加起来。
- 材料颜色取决于反射的红、绿、蓝光的百分数。与光源的特性相似，材料也有环境光、漫反射、镜面反射颜色。

### 10.5.2 光源定义

定义光源主要就是定义它的各种特性。可用下面函数定义：

```
void glLight{if}[v](GLenum light, GLenum pname, TYPE param);
```

- `light` 用形式为 `GL_LIGHTi` 的符号常量表示，0 ≤ i ≤ 7；
- `pname` 设置光源的特性；
- `param` 设置 `pname` 特性的值。

光源定义后，须调用 `glEnable()` 打开该光源。
