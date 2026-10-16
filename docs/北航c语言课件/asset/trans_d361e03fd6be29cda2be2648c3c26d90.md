

## 2. 字符串比较函数strcmp()

**使用形式：** `strcmp(字符串1，字符串2)`

其中，字符串可以是字符串常量或字符数组。

**功能：** 比较两个字符串。

**比较的原则：** 对两个字符串，从左至右逐个将对应字符按其 ASCII 码值大小相比较，直到出现不同的字符或遇到“\0”为止。

> 若设 n=strcmp(字符串1，字符串2)：
> 
> 则：
> - n>0；串1>串2
> - n=0；串1=串2
> - n<0；串1<串2

例如： char str1[20], str2[10]；
（将str1[20]和str2[10]赋初值）

```
if(strcmp(str1,str2)>0) puts(str1);
```

注意： 不能写成 if(str1>str2)

```
n=strcmp("China","Korea");
```

‘C’=067<‘K’=075

“China”<“Korea”, n<0

同理：

“China”>“Canada”,n>0

“computer”>“compare”,n>0

“temperature”=“temp”

## 3.字符串连接strcat()函数

**使用形式：** `strcat(字符数组1，字符串2)`

**功能：** 连接两个字符串，把字符串2连接到字符串1的后面，连接后的字符串放在字符数组1中。

+   **说明：**
+   1. 字符数组1必须足够大以便能够容纳字符串2。
+   2. 连接时只在新串最后保留一个“\0”。
+   3. 字符串2可以是字符串常量或字符数组。

## 4. 字符串复制strcpy()函数

使用形式： strcpy(字符数组1，字符串2)

功能： 将字符串2复制到字符数组1中
（其后自动加一个 ‘\0’）。

说明： (1)字符数组1必须足够大以便能够容纳被复制的字符串。

(2)不能用赋值语句将一个字符串常量或字符数组直接赋值给一个字符数组。

```
例如： char str1[20], str2[20];
strcpy(str1,"hello world");
strcpy(str2,str1);
```

```
例如： char str1[20], str2[20];
str1={"hello"};
str2=str1;
```

## Strcpy使用举例：

```
#include <iostream.h>
#include<fstream.h>
main()
{char filewing[20]="wing.txt",filefuse[20]="fuselage.txt",filetail[20]="tail.txt";
    cout<<"请输入飞机部件类型"<<"\n";
    cout<<"1----机翼"<<"\n";
    cout<<"2----机身"<<"\n";
    cout<<"3----尾翼"<<"\n";
    cin>>numpart;
    switch(numpart)
    case 1: {strcpy(filedes,filewing); break;}
    case 2: {strcpy(filedes,filefuse); break;}
    case 3: {strcpy(filedes,filetail); break; }
    case 4: default;
    ifstream in(filedes,ios::in);
    if(!in){cout<<"cannot open Inputfile "<<"\n";exit(1);}
}
```

## 五、字符串数组应用举例

例1：（例题7.8）统计字符串中的单词数。

```
```c
#include <stdio.h>
main()
{
    char string[81],c;
    int i,num=0,word=0;
    gets(string);
    for(i=0;string[i]!='\0';i++)
        if(string[i]==' ') word=0;
        else if(word==0)
            {word=1;num++;}
    printf("\nThere are %d words.", num);
}
```
```

![](img/7e3448331bc3f721cf3127b2b2f06002_400_0.png)

word=0

s[i]!='\0'

N

I am a boy

Y

s[i]==','

N

word==0

N

Y

word=0
(后面出现新单词)

Y

num++
word=1
(后面是旧单词)

## 学习数组这一章要注意的几个问题：

+   1. 在C语言中数组的下标是从0开始；
+   2. C语言不进行下标的越界检查，不论是在编译阶段还是在运行阶段，这个问题交给程序员。这样就给初学者带来一定的风险。
+   3. 数组名是地址，这在字符串处理中已经看到，这个我们要先强记，以后在讲指针时再详细讲。
+   4. 字符数组在定义时必须考虑到串结束符的位置，因为它要占一个字符的位置。
+   5. 要注意数组初始化的方法与简单变量的区别，特别是字符数组的初始化方法。
+   6. 字符串的操作有许多专用函数，请注意掌握并运用。

## 本章作业： 编写并上机调试下列习题：

7-1 从计算机屏幕上任意输入10个实数，求出其中的最大值、最小值和10个数的算术平均值，并按下列格式在屏幕上打印输出（不得照抄冒泡法）。

The maximum=

The minimum=

The average=

7-2 按以下提示对矩阵a赋初值（不得使用初始化方法赋初值），并将转置后的矩阵b打印输出。

a= ⎛ 1 0 0 0 ⎞
   ⎜ -1 1 0 0 ⎟
   ⎜ -1 -1 1 0 ⎟
   ⎝ -1 -1 -1 1 ⎠

b= ⎛ 1 -1 -1 -1 ⎞
   ⎜ 0 1 -1 -1 ⎟
   ⎜ 0 0 1 -1 ⎟
   ⎝ 0 0 0 1 ⎠

+   - 7-3 以下两题任选一题
+   - 1）求1!+2!+3!+...+10!的和
+   - 2）一个整数，它加上100后是一个完全平方数，该数加上268又是另一个完全平方数，请问该数是多少？（提示：1.在10万以内判断;2.如果一个数的平方根的平方等于该数，这说明此数是完全平方数）

## 二、C函数与C程序结构

+   (1) C程序由一个主函数（main函数）和若干个子函数构成；
+   (2) 主函数调用子函数；
+   (3) 子函数在定义时是并列的；
+   (4) 子函数可相互调用，也可被多次调用。

![](img/7e3448331bc3f721cf3127b2b2f06002_408_0.png)

```
#include<stdio.h>
#include<math.h>
void main()
{
char prime(int);/*函数声明或定义函数原形(Function Prototype)*/
int n;
printf("\nInput an integer:");
scanf("%d",&n);
if(prime(n)=='g')//函数调用
    printf("\n%d is a prime.",n);
else
    printf("\n%d is NOT a prime.",n);
}
```

## //函数定义(Function Definition)

```
char prime(int n) //函数类型、名称，形式参数的定义
{
    //函数体定义
    char flag='g';
    int i,k;
    k=sqrt(n);
    for(i=2;i<=k;i++)
        if(fmod(n,i)==0)
        {
            flag='r';
            break;
        }
    return flag; //返回值
}
```

## 函数调用例：

```
void main()              /* 主函数 */
{
    print_star();       /*调用print_star函数打印*****/
    print_message();    /*调用print_message函数写字*/
    print_star();       /*调用print_star函数打印*****/
}

void print_star()       /*定义print_star函数*/
{
    printf("\n************");
}

void print_message()    /*定义print_message函数*/
{
    printf("\n Hello! ");
}
```

![](img/7e3448331bc3f721cf3127b2b2f06002_411_0.png)

