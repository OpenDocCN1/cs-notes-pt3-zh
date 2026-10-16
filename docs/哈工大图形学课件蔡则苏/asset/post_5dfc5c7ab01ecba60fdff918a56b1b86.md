
## NURBS曲线曲面的定义

则有理B样条的表达式为：

p(t) = [P₀B₀,3(t) + (r/(1−r))P₁B₁,3(t) + P₂B₂,3(t)] / [B₀,3(t) + (r/(1−r))B₁,3(t) + B₂,3(t)]

然后取不同的r值得到各种二次曲线：

![](img/af544efef4a0944fe7b8b5fa26ed5707_764_0.png)

图8.17 由不同有理样条权因子生成的二次曲线段

![](img/af544efef4a0944fe7b8b5fa26ed5707_764_1.png)

图8.18 由有理样条函数生成的第一象限上的圆弧

NURBS曲面可由下面的有理参数多项式函数表示：

p(u,v) = \frac{\sum_{k_1=0}^{n_1}\sum_{k_2=0}^{n_2} w_{k_1,k_2} P_{k_1,k_2} B_{k_1,m_1}(u) B_{k_2,m_2}(v)}{\sum_{k_1=0}^{n_1}\sum_{k_2=0}^{n_2} w_{k_1,k_2} B_{k_1,m_1}(u) B_{k_2,m_2}(v)}

## NURBS曲线曲面的性质

NURBS曲面可由下面的有理参数多项式函数表示：

```
p(t) = Σ_{k=0}^{n} P_k R_{k,m}(t)
```

```
R_{k,m}(t) = w_k B_{k,m}(t) / Σ_{j=0}^{n} w_j B_{j,m}(t)
```

- 普遍性
- 局部性
- 凸包性
- 可微性
- 权因子

## NURBS曲线曲面的特点

- □ 既为自由型曲线曲面也为初等曲线曲面的精确表示与设计提供了一个公共的数学形式，因此，一个统一的数据库就能够存储这两类形状信息。

- □ 为了修改曲线曲面的形状，既可以借助调整控制顶点，又可以利用权因子，因而具有较大的灵活性。

- 计算稳定且速度快。
- **NURBS**有明确的几何解释，使得它对良好的几何知识尤其是画法几何知识的设计人员特别有用。
- **NURBS**具有强有力的几何配套计算工具，包括节点插入与删除、节点细分、升阶、节点分割等，能用于设计、分析与处理等各个环节。

- NURBS具有几何和透视投影变换不变性。
- NURBS是非有理B样条形式以及有理与非有理Bezier形式的合适的推广。
- 需要额外的存储以定义传统的曲线曲面。
- 权因子的不合适应用可能导致很坏的参数化，甚至毁掉随后的曲面结构。

- 某些技术用传统形式比用NURBS工作得更好。
  例如，曲面与曲面求交时，NURBS方法特别难于处理刚好接触的情况。

- 某些基本算法，例如求反曲线曲面上的点的参数值，存在数值不稳定问题。

## 8.6 曲线曲面的转换和计算

- 曲线曲面的转换
- 样条曲线曲面的离散生成

## 曲线曲面的转换

$p(t) = T \cdot M_1 \cdot G_1 \quad p(t) = T \cdot M_2 \cdot G_2$

$p(t) = T \cdot M_1 \cdot G_1 = T \cdot M_2 \cdot G_2$

$G_2 = M_2^{-1} \cdot M_1 \cdot G_1 = M_{1,2} \cdot G_1$

## 以三次周期性B样条变换到三次Bezier样条为例

p(t) = T · M_B · G_B = T · M_be · G_be

G_be = M_be^{-1} · M_B · G_B = M_{B,be} · G_B

M_{B,be} = \begin{bmatrix} 1 & 3 & -3 & 1 \\ 3 & -6 & 3 & 0 \\ -3 & 3 & 0 & 0 \\ 1 & 0 & 0 & 0 \end{bmatrix}^{-1} · \frac{1}{6} \begin{bmatrix} 1 & 3 & -3 & 1 \\ 3 & -6 & 3 & 0 \\ -3 & 0 & 3 & 0 \\ 1 & 4 & 1 & 0 \end{bmatrix} = \frac{1}{6} \begin{bmatrix} 1 & 4 & 1 & 0 \\ 0 & 4 & 2 & 0 \\ 0 & 2 & 4 & 0 \\ 0 & 1 & 4 & 1 \end{bmatrix}

## 三次Hermite样条矩阵： $M_h = \begin{bmatrix} 2 & -2 & 1 & 1 \\ -3 & 3 & -2 & -1 \\ 0 & 0 & 1 & 0 \\ 1 & 0 & 0 & 0 \end{bmatrix}$

## 三次Bezier样条矩阵： $M_{be} = \begin{bmatrix} -1 & 3 & -3 & 1 \\ 3 & -6 & 3 & 0 \\ -3 & 3 & 0 & 0 \\ 1 & 0 & 0 & 0 \end{bmatrix}$

## 三次均匀B样条矩阵： $M_B = \begin{bmatrix} -1 & 3 & -3 & 1 \\ 3 & -6 & 3 & 0 \\ -3 & 0 & 3 & 0 \\ 1 & 4 & 1 & 0 \end{bmatrix}$

## Horner规则

Horner规则是最简单和最直观的规则。该规则通过逐次分解因子来减少计算量。下面以三次样条为例进行说明。

x(t) = aₓ t³ + bₓ t² + cₓ t + dₓ

y(t) = aᵧ t³ + bᵧ t² + cᵧ t + dᵧ

z(t) = a_z t³ + b_z t² + c_z t + d_z

x(t) = ((aₓ t + bₓ) t + cₓ) t + dₓ

## 向前差分计算

向前差分计算是求解多项式函数值最快的方法。它采用了增量算法的思想，利用前次计算出的函数值以及当前的函数值增量来求出当前的函数值，以x坐标值为例

```
x_{k+1} = x_k + Δx_k
```

每步的增量 称为向前差分（Forward Difference）。

## 细分

用少量的控制顶点来设计曲线形状，然后用细分过程来得到附加的控制点，可以对曲线的某些小段作精确的调整。

![](img/af544efef4a0944fe7b8b5fa26ed5707_779_0.png)

图8.19 四个控制点的Bezier曲线分成两段

## Bezier曲线曲面函数

## Bezier曲线曲面的求值函数

```
void glMap1{fd}(GLenum target,
TYPE t1, TYPE t2, GLint stride, GLint
order, const TYPE *points);
```

```
void glMap1{fd}(GLenum target,
TYPE t1, TYPE t2, GLint stride, GLint
order, const TYPE *points);
```

- □ 激活Bezier曲线曲面的求值函数
  
  glEnable(GL_MAP1_VERTEX_3)

- □ 计算沿样条路径的位置并显示曲线或曲面
  
  void glEvalCoord1{fd}(TYPE t);
  glEvalCoord2{fd}(TYPE u, TYPE v);

## B样条曲线曲面函数

□ 如果要对NURBS曲面应用光照，可以调用函数使曲面自动生成面法线。

```
glEnable(GL_AUTO_NORMAL);
```

□ 指定一个NURBS对象，这个对象既可以是曲线也可以是曲面，然后使用函数

```
gluNewNurbsRenderer()
```

当NURBS对象不需要再使用时，可以使用函数删除NURBS对象。

```
gluDeleteNurbsRenderer(curveName);
```

调用函数gluNurbsProperty( )设置 NURBS对象的属性，包括用于渲染的多边形的最大尺寸或线段的最大长度。

```
void gluNurbsProperty(
GLUnurbsObj *nobj, GLenum
property, GLfloat value);
```
