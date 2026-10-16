

## 二、关系表达式

### 1. 什么是关系表达式？

如：(a>b)>(b<c)，‘a’<‘b’，x>y，s+f>d

### 2. 关系表达式的值

运算结果：逻辑值 1或非零—“真”，0—“假”

如：设 a=3，b=2，c=1

求下面关系表达式的值：

- `c>b`：值为 **0**
- `(a-b)==1`：值为 **1**
- `b+c<a`：值为 **0**

> 如果关系运算对象的类型不同，也要先进行类型转换。

## 5.2 逻辑运算符和逻辑表达式

### 一、逻辑运算符及其优先次序

3种逻辑运算符：

优先级

- ① ! （逻辑非）
- ② && （逻辑与）
- ③ || （逻辑或）

(高)

(低)

如： !a        a为真，则!a为假。
a||b        a、b之一为真，则a||b为真。
a&&b        a、b同时为真，则a&&b为真。

## 5.2 逻辑运算符和逻辑表达式

### 一、逻辑运算符及其优先次序

与其它运算符的比较：

(高)

(低)

- 1. ()
- 2. ! , ++, --, -(负号), (类型)
- 3. 算术 *, /, %
- 4. 算术 +, -
- 6. 关系 <, <=, >, >=
- 7. 关系 ==, !=
- 11. 逻辑 &&
- 12. 逻辑 ||
- 14. 赋值运算符
- 15. 逗号运算符

例如： c=d>a+b&&a>b
等效于：
c=((d>(a+b))&&(a>b))

## 5.3 if语句

### 一、if语句的三种形式

### 1. if（表达式）语句

执行过程：当表达式的值为“真”（非零）时，执行语句，否则，不执行语句。

![](img/7e3448331bc3f721cf3127b2b2f06002_226_0.png)

如：`if (x > y) z = x;`

### 2. if (表达式) 语句1
else 语句2

执行过程：当表达式的值为“真”（非零）时，执行语句1，否则，执行语句2。

![](img/7e3448331bc3f721cf3127b2b2f06002_227_0.png)

```
如： if (x>y) z=x ;
else z=y ;
```

- 3. if (表达式1) 语句1  
- else if (表达式2) 语句2  
- else if (表达式3) 语句3  
- ⋮  
- else if (表达式n) 语句n  
- else 语句n+1

![](img/7e3448331bc3f721cf3127b2b2f06002_228_0.png)

```
如：if (grade>=85) level=‘A’；
    else if (grade>=70) level=‘B’；
    else if (grade>=60) level=‘C’；
    else level=‘D’；
```

### if 语句说明：

(1) if 和 else if 后面的表达式一般为逻辑表达式或关系表达式，也可以是任意数值类型表达式。

该语句是合法的：`if(3.0) printf("ok!");`

(2) if 语句中的“语句”为一个简单语句或复合语句。如：下面哪个程序段有错？

```
if (x>=0)
    printf("X= %d\n",x);
    printf("X is positive.\n");
else
    printf("X= %d\n",x);
    printf("X is negative.");
```

```
if (x>=0)
{
    printf("X= %d\n",x);
    printf("X is positive.\n");
}
else
{
    printf("X= %d\n",x);
    printf("X is negative.");
}
```

### 二、if 语句的嵌套

在 if 语句中又包含一个或多个 if 语句，称为

if 语句的嵌套。

一般形式：

```
if(条件1)
    if(条件2)语句1
    else 语句2
else
    if(条件3)语句3
    else 语句4
```

内嵌 if

内嵌 if

如：

```
if(x>0)
    if(y>0)
        printf("x>0,y>0");
    else
        printf("x>0, y<=0");
else
    if(y>0)
        printf("x<=0, y>0");
    else
        printf("x<=0, y<=0");
```

### 说明：

else与if的匹配原则是：一个else应与其之前距离最近且没有与其它else配对的if配对。

```
if(n>=18)
    if(n<60)
        printf("adult");
    else
        printf("minor");
```

```
if (n>=18)
{
    if (n<60) printf("adult");
}
else
    printf("minor");
```

```
if (n>=18)
    if (n<60)
        printf("adult");
    else ;
else
    printf("minor");
```

![](img/7e3448331bc3f721cf3127b2b2f06002_232_0.png)

缩　排

```c
#include <stdio.h>
main()
{
    int x;
    scanf("%d",&x);
    if (x>0)
    {
        printf("X is positive.");
        x=x+1;
    }
    else
        printf("X is negative.");
}
```

### 三、用if 语句实现选择结构举例

例： 求 y = 
{ -1 ;  x<0
  0 ;  x=0
  1 ;  x>0 } 输入x 值，输出y 值。

```
main()
{
    int x,y;
    scanf("%d",&x);
    if(x<0) y=-1;
    else if(x==0) y=0;
    else if(x>0) y=1;
    printf("x=%d y=%d",x,y);
}
```

例：任意输入三个不相等的数，将其按由小到大的顺序输出。

```
main()
{
    float a,b,c,t;
    scanf("%%f%%f%%f",&a,&b,&c);
    if(a>b)
    { t=a;a=b;b=t;}//结果a<b
    if(a>c)
    {t=a;a=c;c=t;}//结果a<c
    if(b>c)
    { t=b;b=c;c=t;}//结果b<c
    printf("%%5.2f,%%5.2f,%%5.2f",a,b,c);//a<b<c
}
```

a=7,b=3

t=a(=7)
a=b(=3)
b=t(=7)

### 注意区别

```
if(season==spring) printf("flower");
else if(season==summer) printf("hot");
else if(season==autumn) printf("fruit");
else printf("snow");
```

```
if(e1) s1;
else if(e2) s2;
else s3;
```

```
if(sex=="male") printf("Man");
if(age>=18) printf("adult");
if(profession=="armyman") printf("PLA");
```

```
if(e1) s1;
if(e2) s2;
if(e3) s3;
```

### 四、条件运算符和条件表达式

### 条件表达式的一般形式：

表达式1 ? 表达式2 : 表达式3　如：(a>b) ? a : b

条件表达式 = {
　表达式2（表达式1为真）
　表达式3（表达式1为假）

C中唯一的三目运算符。目的：简化 if 语句。

```
if (a>b) max=a;
else max=b;
```

若 a=3，b=8，则 max=?

等效于：max= (a>b) ? a : b ;

### 条件运算符的优先级(13级):

算术运算符=>关系运算符=>逻辑运算符(除！)
(3、4级)        (6、7级)        (11、12级)

逗号运算符<=赋值运算符<=条件运算符
(15级)            (14级)

如： x = a+b>c && c>d ? a+b : d

等效于： x =(((a+b)>c) && (c>d)) ? (a+b) : d

### 条件运算符的结合方向：自右至左

如： a>b ? a : c>d ? c : d

等效于： a>b ? a : (c>d ? c : d)

