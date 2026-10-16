

上半部分：$(x_p,y_p),(x_p+1,y_p-0.5)$

$d_1=F(x_p+1,y_p-0.5)=b^2(x_p+1)^2+a^2(y_p-0.5)^2-a^2b^2$

$d_1<0$，中点在椭圆内，取正右方像素。

$d'_1=F(x_p+2,y_p-0.5)=b^2(x_p+2)^2+a^2(y_p-0.5)^2-a^2b^2$

$=d_1+b^2(2x_p+3)$

$d_1>0$，中点在椭圆外，取右下方像素。

$d'_1=F(x_p+2,y_p-1.5)=b^2(x_p+2)^2+a^2(y_p-1.5)^2-a^2b^2$

$=d_1+b^2(2x_p+3)+a^2(-2y_p+2)$

$d_1$ 初值 $d_1^0=F(1,b-0.5)=b^2+a^2(-b+0.25)$

下半部分：$(x_p,y_p)$，下一个点为 $(x_p,y_p-1)$ 或者 $(x_p+1,y_p-1)$。

$M=(x_p+0.5,y_p-1)$

$d_2=F(x_p+0.5,y_p-1)=b^2(x_p+0.5)^2+a^2(y_p-1)^2-a^2b^2$

$d_2<0$，中点在椭圆内，取右下方像素。

$d'_2=F(x_p+1.5,y_p-2)=b^2(x_p+1.5)^2+a^2(y_p-2)^2-a^2b^2$

$=d_2+b^2(2x_p+2)+a^2(-2y_p+3)$

$d_2\ge0$，中点在椭圆外，取正下方像素。

$d'_2=F(x_p+0.5,y_p-2)=b^2(x_p+0.5)^2+a^2(y_p-2)^2-a^2b^2$

$=d_2+a^2(-2y_p+3)$

$d_2$ 初值 $d_2^0=F(x,y)=(b(x+0.5))^2+(a(y-1))^2-a^2b^2$

$(x,y)$ 为交界点。

## 第三节 区域填充

- 种子填充算法
- 多边形扫描转换算法

### 一、种子填充算法

**1. 区域**

区域是指光栅网格上的一组像素。区域填充是把某确定的像素值送入到区域内的所有像素中。

**2. 区域填充方法分为两大类**

- (1) 区域由**多边形**围成，区域由多边形的顶点序列来定义；

  优点：占用内存少；缺点：得区分内外侧。

- (2) 是通过**像素的值**来定义区域的内部。

  优点：形状可任意复杂，可直接着色；缺点：几何意义不直观。

**3. 用像素值定义区域**

- 内定义区域（oldvalue）指出区域内部所具有的像素值（内点表示）。
- 边界定义区域（boundaryvalue），指出区域边界所具有的像素值。此时区域边界上所有像素具有某个边界值 boundaryvalue。区域的边界应该是封闭的，指明区域的内部和外部。

以像素为基础的区域填充主要是依据区域的连通性进行。

**4. 区域的连通性**

- 四连通：从区域中的一个像素出发，经连续地向上下左右四个相邻像素的移动，就可以到达区域内的任意另一个像素。
- 八连通：如果除了要经上下左右的移动，还要经左上、右上、左下和右下的移动，才能由一个像素走到区域中另外任意一个像素。

四连通区域必定是八连通区域，反之不一定。

| 左上 | 上 | 右上 |
|------|----|------|
| 左 | P | 右 |
| 左下 | 下 | 右下 |

**5. 种子填充算法**

**（1）四连通内定义区域填充算法：**

```c
void Floodfill(int x,int y,COLORREF oldvalue,COLORREF newvalue)
/* (x, y) 为种子，oldvalue是原值，newvalue是新值，应不等于原值。 */
{
    if (GetPixel(x,y) == oldvalue)  // 是否在区域内并且尚未被访问过
    {
        SetPixel(x,y,newvalue);
        Floodfill(x,y-1,oldvalue,newvalue); // 上
        Floodfill(x,y+1,oldvalue,newvalue); // 下
        Floodfill(x-1,y,oldvalue,newvalue); // 左
        Floodfill(x+1,y,oldvalue,newvalue); // 右
    }
}
```

优点：算法简单；缺点：重复多。

**（2）四连通边界定义区域填充算法：**

```c
void Boundaryfill(int x,int y,COLORREF boundaryvalue,COLORREF newvalue)

/* (x, y) 为种子位置，boundaryvalue是边界像素值，
   newvalue是区域内像素新值，未填充前区域内不应有值为newvalue的像素。 */
{
    if (GetPixel(x,y) != boundaryvalue
        && GetPixel(x,y) != newvalue)   // 未达边界且未访问过
    {
        SetPixel(x,y,newvalue); // 赋以新值
        Boundaryfill(x,y-1,boundaryvalue,newvalue);
        Boundaryfill(x,y+1,boundaryvalue,newvalue);
        Boundaryfill(x-1,y,boundaryvalue,newvalue);
        Boundaryfill(x+1,y,boundaryvalue,newvalue);
    }
}
```

算法简单，多层递归，存储空间有限 → 堆栈溢出。

演示

**（3）扫描线种子填充算法（适用于边界定义的四连通区域）**

像素段：将区域内由边界点限定的同一行内相连接的不具有新值 newvalue 的一组像素称为一个**像素段**，像素段用它**最右边的像素**来标识。

**算法的步骤如下：**

1. [初始化] 将堆栈置为空，将给定的种子点 (x, y) 压入堆栈。
2. [出栈] 如果堆栈为空，算法结束，否则取栈顶元素 (x, y) 作为种子点。
3. [区段填充] 从种子点 (x, y) 开始沿当前扫描线向左右两个方向逐个像素进行填充，直到遇到边界点为止。
4. [定范围] 用 xl 和 xr 分别表示在步骤 3 中填充的区段的左右两个端点的横坐标。
5. [进栈] 对当前扫描线上下相邻的两条扫描线从右向左地确定位于 [xl, xr] 区域内的像素段。如果区域内的像素已经填充或为边界则转到步骤 2，否则取像素段的右端点作为种子点，压入堆栈，再转到步骤 2。

下面我们用伪 C 语言写出扫描线填充算法。

```c
void ScanlineSeedfill(int x,int y,COLORREF boundaryvalue,COLORREF newvalue)
{
    int x0,xl,xr,y0,xid;
    int flag;
    Stack s;
    Point p;
    s.push(Point(x,y)); // 种子像素入栈
    while(!s.isempty())
    {
        p=s.pop(); // 栈顶像素出栈
        x=p.x; y=p.y;
        SetPixel(x,y,newvalue);
        x0=x+1;
        while(GetPixel(x0,y)!=boundaryvalue) // 填充右方像素
        {
            SetPixel(x0,y,newvalue);
            x0++;
        }
        xr=x0-1; // 最右边像素
        x0=x-1;
        while(GetPixel(x0,y)!=boundaryvalue) // 填充左方像素
        {
            SetPixel(x0,y,newvalue);
            x0--;
        }
        xl=x0+1; // 最左边像素
        // 检查上一条扫描线和下一条扫描线，
        // 若存在非边界且未填充的像素，
        // 则选取代表各连续区间的种子像素入栈。
        y0=y;
        for(int i=1;i>=-1;i-=2) // 从最右像素开始寻找上下两行的像素段
        {
            x0=xr;
            y=y0+i;
            while(x0>=xl)
            {
                flag=0;
                while((GetPixel(x0,y)!=boundaryvalue) &&
                      (GetPixel(x0,y)!=newvalue) && (x0>xl))
                {
                    if(flag==0)
                    {
                        flag=1; // 标志找到新的像素段
                        xid=x0;
                    }
                    x0--;
                }
            }
        }
    }
}
```
