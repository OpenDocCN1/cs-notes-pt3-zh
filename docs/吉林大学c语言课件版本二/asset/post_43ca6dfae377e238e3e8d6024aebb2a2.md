
/*计算一个顶点坐标*/
void coordinate(float r, float theta) {
    /* 先把“角度”转换成“弧度”，再转换成直角坐标 */
    px=r*cos(PI*theta/180);
    py=r*sin(PI*theta/180);
}

/*求三个交点*/
void three_inter(){
    intersection(xa, ya, xb, yb, xd, yd, xe, ye);
    b1_x=wx;  b1_y=wy;
    intersection(xb, yb, xc, yc, xe, ye, xf, yf);
    b2_x=wx;  b2_y=wy;
    intersection(xc, yc, xd, yd, xf, yf, xa, ya);
    b3_x=wx;  b3_y=wy;
}

/*已知四点，求两条直线交点*/
void intersection(float rx, float ry, float sx, float sy, float tx, float ty, float ux, float uy){
    equation (rx, ry, sx, sy, tx, ty, ux, uy);
    inter (l1_a, l1_b, l2_a, l2_b);
}

```c
/*已知四点，求两条直线方程*/

void equation ( float rx, float ry, float sx, float sy,
                float tx, float ty, float ux, float uy){
    straightline(rx, ry, sx, sy);
    l1_a=a;    l1_b=b;
    straightline(tx, ty, ux, uy);
    l2_a=a;    l2_b=b;
}
```

/*计算由两点确定直线方程的斜率（a）和截距（b）*/
void straightline(float ex, float ey, float fx, float fy){
    a=(fy-ey)/(fx-ex); /* 斜率 */
    b=ey-a*ex;    /* 截距 */
}

/*已知两个直线方程的斜率和截距，求它们交点*/
void inter ( float ma, float mb, float na, float nb){
    wx=(nb-mb)/(ma-na);
    wy=ma*wx+mb;
}

/* 检验 */

bool test ( float b1_x, float b1_y,
            float b2_x, float b2_y,
            float b3_x, float b3_y) {
    straightline(b1_x, b1_y, b2_x, b2_y);
    if(fabs(b3_y-(a*b3_x+b))<eps)
        return true;
    else
        return false;
}

## 本章小结

- 函数的定义
- 函数的程序设计思想
- 函数的调用

## 作业

- ① 4.1
- ② 4.8
- ③ 4.12

## 第五章 流程控制

- 顺序结构
- 分支结构
- 循环结构
- 程序设计实例
- 本章小结

## 顺序结构

- 属性
  - 某部分若执行，则语句顺序全部被执行
  - 若不执行，则全部语句一个也不执行
- 形式
  {
  DS
  DS
  ... ...
  DS
  }

## 分支结构

MAX(A, B) = { A    当 A > B
               B    当 A ≤ B }

## 逻辑分支结构

<if语句> → if ( <表达式> ) <语句>
| if ( <表达式> ) <语句> else <语句>

- if (e) S1 else S2
- if (e) S1

## 执行过程与PAD图

```
if (e)
S1
else
S2
```

![](img/e9111c49b068ca3c37fc762f47ecac61_221_0.png)

## 例5.1

![](img/e9111c49b068ca3c37fc762f47ecac61_222_0.png)

```
float max ( float a, float b ) {
    if (a>b)
        return a;
    else
        return b;
}
```

## 形式二

if ( e )

S

![](img/e9111c49b068ca3c37fc762f47ecac61_223_0.png)

## if语句应注意的问题

- 布尔表达式
- 可以嵌套
- else归属问题

```
if (a>b) if (b>c) x=0; else x=1;
```

![](img/e9111c49b068ca3c37fc762f47ecac61_224_0.png)

■ else 属于最前边的 if，则

```
if (a>b) if (b>c) x=0; else x=1;
```

![](img/e9111c49b068ca3c37fc762f47ecac61_225_0.png)

■ 前述的问题的答案是：

- ① 若 a<=b 执行 `x = 1;`
- ② 若 a>b 且 b<=c 什么也不执行

else 属于第二个 if，则
if (a>b) if (b>c) x=0; else x=1;相当于

```
if ( a>b ) {
    if (b>c)
        x = 0;
    else
        x = 1;
}
```

![](img/e9111c49b068ca3c37fc762f47ecac61_226_0.png)

上述的问题的答案是

- ① 若 a<=b 什么也不执行；
- ② 若 a>b 且 b<=c 执行 x = 1。

## 两义性

- C标准规定：
- else部分与前面最邻近的一个没有配对的 if 配对
- 第二种方案解释。
- 若想描述第一种方案的结构只好用 {、} 将中间的 “if() 语句” 括起来，构成复合语句。

```
if (a>b) {if (b>c) x=0}; else x=1;
```

![](img/e9111c49b068ca3c37fc762f47ecac61_227_0.png)

## 例5.3 求方程 ax² + bx + c = 0 的根

```
x = (-b ± √(b² - 4ac)) / 2a
```

- ① 是一元二次方程(a≠0)
  - 有实根(Δ≥0)
    - 两个不同的实根(Δ>0)
    - 两个相同的实根(Δ=0)
  - 有虚根(Δ<0)
- ② 是一元一次方程(a=0, b≠0)
- ③ 是恒等式(a=0, b=0)
  - 恒等式成立(c=0)
  - 恒等式不成立(c≠0)

## 解二次方程

读入 a,b,c

计算Δ

二次方程
Δ>0

二实根:x1,x2

两实根:x1=x2

Δ=零则

两虚根:x1,x2

求解 x1, x2

一次方程
b≠0

x为c加程

常数0方程

退化0=0

矛盾c=0

输出 x1,x2

# 结束

## 演示例5.3程序

```c
if(a!=0){
delta=b*b-4*a*c;
if(delta>0)
printf("x1=%g ,x2=%g\n", (-b+sqrt(delta))/(2*a),(-b-sqrt(delta))/(2*a));
else
if(delta==0)
printf("x1=x2=%f\n",-b/(2*a));
else
printf("x1=%g+%gi ,x2=%g-%gi\n", -b/(2*a),sqrt(-delta)/(2*a), -b/(2*a),sqrt(-delta)/(2*a) );
}else{ // 以下处理a==0的情况
if(b!=0)
printf("x=%g\n",-c/b);
else
if(c==0)
printf("0=0!\n");
else
printf("%g=0\n",c);
}
```
