
## C语言中的选择语句有两种：

双分支选择语句  if

多分支选择语句  switch

## 4.3 if语句

### 1. if语句的最简单形式：

if (表达式) 语句

执行过程：

- 首先先判断表达式的值
- 若为非0则执行语句
- 若为0则跳过该语句

if语句的简单形式，在语法上视为一条语句。

![](img/609af85bac45577917bd36819bca122b_97_0.png)

## 例：计算分段函数 y = { 3 - x  (x < 0)  2x  (x ≥ 0) }

```
main()
{ float x , y;
    scanf("%%f", &x);
    y = 2 * x;
    if ( x < 0 )  y = 3 - x;
    printf("y= %.2f", y);
}
```

## 例：计算分段函数 y = { 3 - x  (x < 0)  2x  (x ≥ 0) }

```
main()
{ float x , y;
    scanf("%f", &x);
    if ( x < 0 ) y = 3 - x ;
    else y = 2 * x ;
    printf("y= %.2f", y );
}
```

## 例： 输入两个数,比较其大小，将较大的数输出。

算法分析：

- (1) 输入两个数据a,b；
- (2) 如果a>b 则输出a； 否则，输出b。

```
#include <stdio.h>
main()
{
    float a, b;
    scanf("%f, %f",&a, &b);
    if (a>b) printf("%f", a);
    else     printf("%f", b);
}
```

if语句的语句1和语句2又称为if的执行语句。if的执行语句在语法上是一条语句，可以是任何类型的语句，简单语句、复合语句、空语句、流程控制语句都可以作为if的执行语句。

下面我们通过一个例子分别介绍用不同的语句作为if的执行语句的情形：

例：计算分段函数：

```
y = {
  2*x    x<=-10
  2+x    -10<x<=0
  x-2    0<x<=10
  x/10   x>10
}
```

## 方法一：用简单语句

![](img/609af85bac45577917bd36819bca122b_103_0.png)

```
#include<stdio.h>
main()
{
    float x,y;
    scanf("%f",&x);
    if(x<=-10) y=2*x;
    if(-10<x&&x<=0) y=2+x;
    if(0<x&&x<=10) y=x-2;
    if(x>10) y=x/10;
    printf("\ny=%f",y);
}
```

## 方法二：用if语句做语句2

```
#include<stdio.h>
main()
{ float x,y;
    scanf("%f",&x);
    if(x<=-10) y=2*x;
    else  if(x<=0) y=2+x;
        else if(x<=10) y=x-2;
        else y=x/10;
    printf("\ny=%f",y);
}
```

这种用if语句作为上一级if语句的语句2的结构，称为if语句的多分支选择结构。

## 多分支选择语句一般形式：

```
if (表达式) 语句1
else if (表达式) 语句2
else ...
```

流程图如左：

- 先判断表达式1的值
- 为0就执行下一个判断
- 非0就执行下面的语句
- 一直这样做下去
- 直到得出最后结果

![](img/609af85bac45577917bd36819bca122b_105_0.png)

## if 语句的二层嵌套结构如下：

if (表达式1)
    if (表达式1_2)  语句1_1
    else           语句1_2
else
    if (表达式2_1)  语句2_1
    else           语句2_2

![](img/609af85bac45577917bd36819bca122b_107_0.png)

## if语句编程举例：

例1.写一个程序完成下列功能：

- 输入一个分数score
- 当 score<60 输出 E
- 当60<=score <70 输出 D
- 当70<=score <80 输出 C
- 当80<=score <90 输出 B
- 当90<=score 输出 A

## 程序如下：

```c
#include <stdio.h>
main()
{
    float score;
    scanf("%f", &score);
    if (score<60) printf("%c", 'E');
    else if (score<70) printf("%c", 'D');
    else if (score<80) printf("%c", 'C');
    else if (score<90) printf("%c", 'B');
    else printf("%c", 'A');
}
```

## 例2： 编程实现：根据两个数sex和tall分类，如果 sex为’ F’，当tall大于等于150时，输出 A，否则输出 B；若sex不为’ F’，当tall大于等于170时，输出A，否则输出B。

## 分析：

- 根据sex分支
- 在sex为’ F’的分支中判断tall是否>=150
- 在sex不为’ F’的分支中判断tall是否>=170

## 程序如下：

```
#include<stdio.h>
main()
{
    int tall; char sex;
    printf("input sex and tall : ");
    scanf("%c %d", &sex, &tall );
    if (sex=='F')
        if (tall>=150)  printf(" A ");
        else printf(" B ");
    else
        if (tall>=170)  printf(" A ");
        else printf(" B ");
```

## 4.4 Switch语句

if语句是根据表达式的值是否为0来判断执行哪一分支的，某些情况下，要根据表达式的不同值来判断执行哪一分支，如表达式的值为‘a’,‘b’,‘c’时，分别执行不同的操作。虽然也可以用多条if语句来完成这一工作，但c语言中提供了一条switch语句，可以更方便的完成。

## Switch语句的基本形式：

```c
switch(表达式)
{
    case 常量1：语句块1；
    case 常量2：语句块2；
    ……………………
    case 常量n：语句块n；
    default：语句块n+1；
}
```

其中每个语句块都可以是0到多条语句，可以有选择的包含或不包含结束语句break；注意：case后面的值不能为变量。

## 执行过程：

> 先计算表达式的值，判断与case后的哪个常量值相等，若与常量的值相等，则从语句块i开始执行，直到遇到第一条break语句结束，或执行完语句块n+1结束。若与任何一个常量的值都不相等，直接执行语句块n+1。

例：看下面的程序在几种不同输入情况下的输出：

```
#include<stdio.h>
main()
{ char i;
scanf("%c",&i);
switch(i)
{ case ‘a’: i++;printf("%c",i);break;
case ‘b’: i++;printf("%c",i);
default: i=i+2;printf("%d",i);
}
}
```

- 1. 输入： a
- 2. 输入： b
- 3. 输入： c

- 输出： b
- 输出： c101
- 输出： 101

## 例： 编程：根据输入的学生的成绩判断等级。当成绩 score ≥90时为 A等；成绩 70≤score <90 为B等；成绩 60≤score <70 为C等；成绩 score < 60 为D等 (score 为整数)。

分析：设 score 为整型数，利用两个整数相除，结果自动取整的特性， score 和 score /10 有如下对应关系：

| score | score/10 |
| --- | --- |
| 90以上 | 10, 9 |
| 70~89 | 7, 8 |
| 60~69 | 6 |
| 60以下 | 5, 4, 3, 2, 1, 0 |

因此,可以用 score /10 的值来确定分支。
