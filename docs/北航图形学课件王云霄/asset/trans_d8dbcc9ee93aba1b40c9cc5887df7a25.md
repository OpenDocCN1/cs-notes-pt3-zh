

```cpp
//将最右侧可填充像素压入栈中
if(flag==1)
{
    s.push(Point(xid,y));
    flag=0;
}
//检查当前填充行是否被中断，若被中断，寻找左方第一个可填充像素
//判断当前点是否为边界点//判断当前点是否为已填充点
while((GetPixel(x0,y)==boundaryvalue) ||
      (GetPixel(x0,y)==newvalue))
    x0--;//若当前点为边界点或已填充点，根据前面的判断，当前点必然未超出左边界，则当前点向左移动
}//while(x0>=xl)
}//for(int i=1;i>=-1;i-=2)
}//while(!s.isempty())
}
```

![](img/4628856fffb4db710a3ae3a299935a63_95_0.png)

## 二、多边形的扫描转换算法

“奇偶”性质：即一条直线与任意封闭的曲线相交时，总是从第一个交点进入内部，再从第二个交点退出，以后交替地进入、退出，即奇数次进入，偶数次退出。当然可能有一些“相切”的点应特殊处理。

### 扫描转换法步骤：

- 1. 找出扫描线与多边形边界线的所有交点；
- 2. 按 x 坐标增加顺序对交点排序；
- 3. 在交点对之间进行填充。（偶数）

### 奇异顶点：

- 局部极大或局部极小点，交点看做是二个；
- 非局部极值点，交点看做一个。

![](img/4628856fffb4db710a3ae3a299935a63_98_0.png)

对非极值的简便处理

### step1．如何计算扫描线与多边形边界线的所有交点？

若扫描线 $y_i$ 与多边形边界线交点 $x$ 的坐标是 $x_i$，则对下一条扫描线 $y_{i+1}$，它与那条边界线的交点的 $x$ 坐标 $x_{i+1}$，可如下求出：

$$m=\frac{y_{i+1}-y_i}{x_{i+1}-x_i},\quad y_{i+1}=y_i+1\Rightarrow x_{i+1}=x_i+\frac{1}{m}$$

活跃边：与当前扫描线相交的边。

活跃边表 AET：存储当前扫描线相交的各边的表。

| y_max | x | 1/m | next |
|---|---|---|---|
- y_max：当前这条边的上端点的 y 坐标
- x：当前边与扫描线交点的 x 坐标
- 1/m：当前边的斜率的倒数
- next：指向下一条边的指针

### 边表 ET：记录多边形的所有边

“吊桶”：记录一条边的信息。

| Ymax | Xmin | 1/m | next |
|---|---|---|---|
- Ymax：边的另一端点的较大的 y 坐标
- Xmin：与较小的 y 坐标对应的边的端点的 x 坐标
- 1/m：斜率的倒数
- next：指向下一条边的指针

### Polygonfill(EdgeTableET, COLORREF color)

```
{
    1. y=置y为边表ET中各登记项对应的y坐标中最小的值;

    2. 活跃边表AET初始化为空表;

    3. 若AET非空或ET非空，则执行下列各步，否则算法结束;
    {
        3.1. 将ET中登记项y对应的各“吊桶”合并到表AET中，将AET中各吊桶按x坐标递增排序；
        3.2. 在扫描线y上，按照AET表提供的x坐标对，用color实施填充；
        3.3. 将AET表中有y=y_max的各项清除出表；
        3.4. 对AET中留下的各项，分别将x换为x+1/m，求出AET中各边与下一条扫描线交点的x坐标；
        3.5. y=y+1，返回步骤3处理下一条扫描线。
    }
}
```

![](img/4628856fffb4db710a3ae3a299935a63_104_0.png)

坐标点标注：$(2,9)$、$(2,8)$、$(2,5)$、$(4,8)$、$(7,7)$、$(7,1)$、$(13,11)$、$(13,8)$、$(13,5)$。

线段标注：$l_1$、$l_2$、$l_3$、$l_4$、$l_5$、$l_6$。

### ET：

![](img/4628856fffb4db710a3ae3a299935a63_105_0.png)

### AET指针

初始化 λ

扫描线 1

扫描线 2

扫描线 3

扫描线 4

扫描线 5

扫描线 6

扫描线 7

扫描线 8

扫描线 9

扫描线 10

扫描线 11

扫描线 12 λ

## 第二章 作业

P₂₆₋₃ 方法一：分几种情况来讨论

- (1) 若 |m|<1，则若 x₁ > x₂，则 x₁ ↔ x₂，y₁ ↔ y₂；
  若 |m|>1，则若 y₁ > y₂，则 x₁ ↔ x₂，y₁ ↔ y₂。
- (2) 处理特殊情况（水平垂直线）：
  - 若 x₁ = x₂，则 yₛ = min(y₁, y₂)，yₑ = max(y₁, y₂)；
    `for(y = yₛ; y <= yₑ; y++)` 垂直线段 `setpixel(x, y)`
  - 若 y₁ = y₂，则 xₛ = min(x₁, x₂)，xₑ = max(x₁, x₂)；
    `for(x = xₛ; x <= xₑ; x++)` 水平线段 `setpixel(x, y)`

(3) -1 < m < 0

$(x_i, y_i) \rightarrow (x_i + 1, y_i)$ 或者 $(x_i + 1, y_i - 1)$

$|d_1| = |y - y_i| = y_i - y = y_i - (m x_{i+1} + b)$

$|d_2| = y - (y_i - 1) = m x_{i+1} + b - (y_i - 1)$

$|d_1| - |d_2| = -2 m x_{i+1} - 2 b + 2 y_i - 1$

$p_i = \Delta x (|d_1| - |d_2|) = -2 \Delta y x_i + 2 \Delta x y_i - 2 \Delta y - 2 b \Delta x - \Delta x$

若 $p_i \geq 0$，下一个点应取 $(x_i + 1, y_i - 1)$；若 $p_i < 0$，下一个点应取 $(x_i + 1, y_i)$。

$p_{i+1} - p_i = -2 \Delta y (x_{i+1} - x_i) + 2 \Delta x (y_{i+1} - y_i)$

若 $p_i \geq 0$，$p_{i+1} = p_i - 2 \Delta y - 2 \Delta x$；若 $p_i < 0$，$p_{i+1} = p_i - 2 \Delta y$。

$\because -1 < m < 0$，$m = \Delta y / \Delta x$，$\Delta y < 0$

$p_i \geq 0$ 时，$p_{i+1} = p_i + 2 |\Delta y| - 2 |\Delta x|$，取 $y_i - 1$；

若 $p_i < 0$，$p_{i+1} = p_i + 2 |\Delta y|$，取 $y_i$。

[准备]：$dx \leftarrow |x_2 - x_1|$，$dy \leftarrow |y_2 - y_1|$，$p \leftarrow 2dy - dx$

若 $y_1 < y_2$，则 $s \leftarrow 1$（$0 < m < 1$）；否则 $s \leftarrow -1$（$-1 < m < 0$）。

2.3. 若 $p \ge 0$，则 $y \leftarrow y + s$，$p \leftarrow p + 2(dy - dx)$；否则 $p \leftarrow p + 2dy$。

(4)

$|m| > 1$，具体看 $m > 1$。

$y = mx + b$，$x = \frac{1}{m} y - \frac{b}{m} \Rightarrow x = m' y + b'$

$\therefore 0 < m' < 1$，与 $y = mx + b$ 相比只是 $x \leftrightarrow y$，$m' = \frac{1}{m}$。

$\therefore$ 可用书上的算法，只是 $x$、$y$ 位置互换，$\Delta x$、$\Delta y$ 的位置互换。

### 具体算法如下：

- 1. [准备] 最开始的 (1)、(2)
  - $x \leftarrow x_1$，$y \leftarrow y_1$，$dx \leftarrow |x_2 - x_1|$，$dy \leftarrow |y_2 - y_1|$
  - 若 $m > 0$，则 $s = 1$，否则 $s = -1$
  - 若 $dy > dx$，则 $dx \leftrightarrow dy$，$t = 1$（$|m| > 1$）；否则 $t = 0$（$|m| < 1$）
  - $p \leftarrow 2dy - dx$，$i \leftarrow 1$
- 2. [逐点画线] 若 $i > dx$，则算法结束，否则做以下各步：
  - 2.1 `setpixel(x, y)`，$i \leftarrow i + 1$
  - 2.2 若 $t = 1$（$|m| > 1$），则 $y \leftarrow y + 1$；否则 $x \leftarrow x + 1$（$|m| < 1$）
  - 2.3 若 $p \ge 0$，则若 $t = 1$（$|m| > 1$），则 $x \leftarrow x + s$，$p \leftarrow p + 2(dy - dx)$；若 $t = 0$（$|m| < 1$），则 $y \leftarrow y + s$，$p \leftarrow p + 2(dy - dx)$；否则 $p \leftarrow p + 2dy$
  - 2.4 返回第 2 步开头

