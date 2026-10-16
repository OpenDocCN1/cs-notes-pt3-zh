

# 例：输入3个数，把其中最大的数输出

```
main()
{
    int a,b,c,t,max;
    scanf("%d%d%d",&a,&b,&c);
    t=(a>b) ? a : b ;
    max=(t>c) ? t : c ;
    printf("max=%d\n",max);
}
```

```
或者
max=(a>b) ? a : b ;
max=(max>c) ? max : c ;
或者
max=a;
max=(max>b) ? max : b ;
max=(max>c) ? max : c ;
```

## 5.4 switch 语句

一般形式：

```
switch (表达式)
{
    case 常量表达式1: 语句序列1 [break;]
    case 常量表达式2: 语句序列2 [break;]
    :
    case 常量表达式n: 语句序列n [break;]
    [default : 语句序列n+1]
}
```

// default——缺省

## 执行过程：

![](img/7e3448331bc3f721cf3127b2b2f06002_241_0.png)

## 例：

```c
char grade;
......
switch(grade)
{
    case 'A' : printf("85~100    ");
    case 'B' : printf("70~84     ");
    case 'C': printf("60~69     ");
    case 'D':printf("<60       ");
    default : printf("error ");
}
```
```

若grade='A'，输出结果是什么？

85~100　70~84　60~69　<60　error

## 用break语句处理后的程序段：

```c
switch(grade)
{
    case 'A'：printf("85~100 "); break;
    case 'B'：printf("70~84 "); break;
    case 'C'：printf("60~69 "); break;
    case 'D'：printf("<60 "); break;
    default：printf("error ");
}
```
```

若grade='A'，输出结果又是什么？

**85~100**

## 完整程序：

```
main()
{
    char grade;
    printf("Input grade(A,B,C,D):");
    scanf("%c",&grade);
    switch(grade)
    {
        case'A' : printf("85~100 "); break;
        case 'B' : printf("70~84 "); break;
        case 'C' : printf("60~69 "); break;
        case 'D' : printf("<60 "); break;
        default : printf("error ! ");
    }
}
```

流程图为：

grade

输出
“85—100”

输出
“70-84”

输出
“60-69”

输出
“<60”

输出
“error”

break;
中断switch

## 5.5 选择结构程序举例

## 例1　写程序，判断某一年是否闰年。

![](img/7e3448331bc3f721cf3127b2b2f06002_246_0.png)

设：`leap`代表闰年信息，`leap=1`闰年，`leap=0`非闰年

## 编程一（采用复合运算表达式）：

```c
main()
{
    int year, leap=0;
    scanf("%d", &year);  /* 输入年份值 */
    if ((year%4==0&&year%100!=0)||(year%400==0))
        leap=1;
    else leap=0;
    if(leap == 1) printf("%d is leap", year);
    else printf("%d is not leap", year);
}
```

算术运算符=>关系运算符=>逻辑运算符(除！)

赋值运算符<=条件运算符

## 原程序段

```
If (T>=180&&M1>=60&&M2>=60 || T>=200)
    printf(" Admitted\n");
else
    printf(" Not admitted\n");
```

不使用采用复合运算表达式，改写上述程序段。

## 修改一

```
If (T>=200)
    printf(" Admitted\n");
else if(T>=180)
    if(M1>=60)
        if(M2>=60)
            printf(" Admitted\n");
        else
            printf(" Not admitted\n");
    else
        printf(" Not admitted\n");
else
    printf(" Not admitted\n");
```

## 修改二

```
If (T>=200)
    printf(" Admitted\n");
else if(T<180)
    printf(" Not admitted\n");
else if(M1<60) //M1<60
    printf(" Not admitted\n");
else if(M2<60) //M2<60
    printf(" Not admitted\n");
else printf(" Admitted\n");
//T>=180, M1>=60, M2>=60
```

## 例5.7 已知基本运费、货重，以及路程(s)和折扣的关系标准如下：

| 路程 s | 折扣 |
|---|---|
| s＜250km | 没有折扣 |
| 250≤s＜500 | 2%折扣 |
| 500≤s＜1000 | 5%折扣 |
| 1000≤s＜2000 | 8%折扣 |
| 2000≤s＜3000 | 10%折扣 |
| s≥3000 | 15%折扣 |

编程，计算运费f。

设基本运费p、货物重量w、距离s和折扣d。则总运费的计算公式为： f=p*w*s*(1-d)

算法：先按距离的250倍数进行分类，求每类的折扣，再按公式计算。

## 总运费的计算公式为： f=p*w*s*(1-d)

折扣的变化点都是250的倍数。
c=s/250 代表250的倍数。

![](img/7e3448331bc3f721cf3127b2b2f06002_251_0.png)

```
case 6:                 /*1500≤s<1750*/
case7: d=8 ; break ; /*1750≤s<2000*/      <8
case8:                 /*2000≤s<2250*/      ≥8
case9:                 /*2250≤s<2500*/
case10:                /*2500≤s<2750*/
case11: d=10 ; break; /*2750≤s<3000*/      <12
case12: d=15 ; break; /*3000≤s*/             ≥12
}
f=p*w*s*(1-d/100.0) ;
printf("freight=%15.4f",f) ;
}
```

运行情况： 输入： 10,20,300✓
结果： freight= 58800.0000

若用if 语句实现上述功能，程序为：

```
main()
{ int s;
float p, w, d , f ;
scanf("%%f , %%f , %%d", &p, &w, &s);
if(s>=3000) d=15;
else if (s>=2000&&s<3000) d=10;
else if (s>=1000&&s<2000) d=8;
else if (s>=500&&s<1000) d=5;
else if (s>=250&&s<500) d=2;
else d=0;
f=p*w*s*(1-d/100.0) ;
printf("freight=%%15.4f", f) ;
}
```

