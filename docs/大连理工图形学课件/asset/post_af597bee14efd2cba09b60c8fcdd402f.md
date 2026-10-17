

## 1) Bresenham的基本原理

- 如果直线的（起）端点在整数点上，误差项 d 的初值：d0=0
- x坐标每增加 1，d的值相应递增直线的斜率值 k，即：d=d+k
- 一旦 d≥1，就把它减去 1，保证 d的相对性，且在 0-1之间。

![](img/5541ff2dee1295469371f6f6fbf4c05f_114_0.png)

## 第 2 章 基本图形生成算法（I）

- 令 e=d-0.5，关于 d 的判别式和初值可简化成：
  - e的初值 e0= -0.5，增量亦为 k；
  - e<0时，取当前象素 (xi,yi)的右方象素 (xi+1,yi)；
  - e>0 时，取当前象素（xi,yi）的右上方象素 (xi+1,yi+1)；
  - e=0时，可任取上、下光栅点显示。

![](img/5541ff2dee1295469371f6f6fbf4c05f_115_0.png)

## 1) Bresenham的基本原理

Bresenham算法的构思巧妙：它引入动态误差 e，当 x 方向每次递增 1 个单位，可根据 e 的符号决定 y 方向每次递增 0 或 1。

- e<0，y方向不递增
- e>0，y方向递增 1
- x方向每次递增 1 个单位，e = e + k

## 1) Bresenham的基本原理

因为e是相对量，所以当e>0时，表明e的计值将进入下一个参考点（上升一个光栅点），此时须：e=e-1

![](img/5541ff2dee1295469371f6f6fbf4c05f_117_0.png)

## 2) Bresenham算法的实施 —— Rogers 版

- 通过 (0,0)的所求直线的斜率大于 0.5，它与x=1直线的交点离 y=1直线较近，离 y=0直线较远，因此取光栅点 (1,1)比 (1,0)更逼近直线；
- 如果斜率小于 0.5，则反之；
- 当斜率等于 0.5，没有确定的选择标准，但本算法选择 (1,1)。

![](img/5541ff2dee1295469371f6f6fbf4c05f_118_0.png)

![](img/5541ff2dee1295469371f6f6fbf4c05f_118_1.png)

## 2) Bresenham算法的实现 ——Rogers 版

//Bresenham's line restertization algorithm for the first octal.
//The line end points are (xs,ys) and (xe,ye) assumed not equal.
// Round is the integer function.
// x,y, Δ x, Δ y are the integer, Error is the real.
//initialize variables

x=xs
y=ys
Δx = xe -xs
Δy = ye -ys
//initialize e to compensate for a nonzero intercept
Error =Δ y/Δx-0.5

## 第 2 章 基本图形生成算法（I）

## 2) Bresenham算法的实施 —— Rogers 版

```
```text
//begin the main loop
for i=1 to Δx
        WritePixel (x, y, value)
        if (Error ≥ 0) then
                y=y+1
                Error = Error -1
        end if
        x=x+1
        Error = Error +Δ y/Δx
next i
finish
```
```

提问学生 why？

## 3)整数 Bresenham算法

- 上述 Bresenham算法在计算直线斜率和误差项时要用到浮点运算和除法，采用整数算术运算和避免除法可以加快算法的速度。
- 由于上述 Bresenham算法中只用到误差项（初值 Error =Δ y/Δx-0.5）的符号
- 因此只需作如下的简单变换：NError = 2*Error*Δx
- 即可得到整数算法，这使本算法便于硬件（固件）实现

## 3)整数 Bresenham算法

//Bresenham's integer line rasterization algorithm
for the first octal.
//The line end points are (xs,ys) and (xe,ye) assumed
not equal. All variables are assumed integer.
//initialize variables
x=xs
y=ys
Δx = xe -xs
Δy = ye -ys
//initialize e to compensate for a nonzero intercept
NError =2*Δ y-Δx

> ( Error =Δ y/Δx-0.5 )

## 第 2 章 基本图形生成算法（I）

## 3)整数 Bresenham算法

```
//begin the main loop
for i=1 to Δx
WritePixel (x, y)
if (NError >=0) then
y=y+1
NError = NError -2*Δx 
(Error = Error -1 )
end if
x=x+1
NError = NError +2*Δ y 
(Error = Error +Δ y/Δx )
next i
finish
```

## 4)一般 Bresenham算法算法

- 要使第一个八卦的 Bresenham算法适用于一般直线，只需对以下 2点作出改造：
- 当直线的斜率 |k|>1时，改成 y的增量总是 1，再用 Bresenham误差判别式确定 x变量是否需要增加 1；
- x或 y的增量可能是 “+1”或 “-1”，视直线所在的象限决定 。

## 第 2 章 基本图形生成算法（Ⅰ）

```
```
//Bresenham's integer line resterization algorithm for all quadrants
//The line end points are (xs,ys) and (xe,ye) assumed not equal. All variables
are assumed integer.
//initialize variables
x=xs
y=ys
Δx = abs(xe -xs)
Δy = abs(ye -ys)
sx = isign(xe -xs)
sy = isign(ye -ys)
//Swap Δ x and Δ y depending on the slope of the line.
if Δy>Δx then
    Swap(Δx,Δy)
    Flag=1
else
    Flag=0
end if
```
```

```
//initialize the error term to compensate for a nonzero
intercept
NError =2*Δy-Δx
//begin the main loop
for i=1 to Δx
WritePixel(x, y , value)
if (NError>=0) then
if (Flag) then //Δy>Δx
x=x+sx
else
Y=Y+1
y=y+sy
end if // End of Flag
NError = NError -2*Δx
end if // End of NError
```

## 4)一般 Bresenham算法算法

```
if (Flag) then //Δy>Δ x
y=y+sy
else
x=x+sx
end if
NError = NError +2*Δy
next i
finish
```

## 2.2 圆光栅化算法

### 2.2.1利用圆的八方对称性画圆

- 对圆的分析均假定圆心在坐标原点，因为即使圆心不在原点，可以通过一个简单的平移即可，而对原理的叙述却方便了许多
- 即考虑圆的方程为： \( x^2 + y^2 = R^2 \)

## 2.2.1利用圆的八方对称性画圆利用圆的八方对称性画圆

# void CirclePoints (int x,int y, int value)

WritePixel (x, y, value);
WritePixel (-x, y, value);
WritePixel (-x, -y, value);
WritePixel (x, -y, value);
WritePixel (y, x, value);
WritePixel (-y,x, value);
WritePixel (-y, -x, value);
WritePixel (y, -x, value);

![](img/5541ff2dee1295469371f6f6fbf4c05f_129_0.png)

显然，当x=0或x=y或y=0时，圆上的对称点只有4个，因此，CirclePoints()需要修正。

