
```
```c
for (n=3;n<=1000;n++)
{
    s=0;
    k=n/2+1;
    for (m=1;m<k;m++)
        if (n%m==0)
            ________;
        if (s==n)
        {
            ____________________
        }
}
printf("\nThe sum=%d",sum);
}
```

2．以下程序求[10,1000]之间能被3或5或8整除的数之和。请将程序补充完整，给出正确程序运行结果，填入相应窗口。

```
```c
#include <conio.h>
#include <stdio.h>
#include <math.h>
main()
{
    ____________
    long sum;
    sum=0;
    for (i=10;i<=1000;i++)
    {
        if (____________)
            sum+=i;
    }
    clrscr();
    printf("%ld\n",sum);
}
```

3: 下面程序求[3,750]之间同构数之和，请将程序补充完整，并给出正确结果，填入相应窗口。同构数是：一自然数平方的末几位与该数相同时，称此数为自构数，例如：5*5=25，则称5为自同构数。

```
#include <conio.h>
#include <stdio.h>
#include <math.h>
main()
{
    long sum,n,m,s,k;
    sum=0;
    for (n=3;n<=750;n++)
    {
        if (n<10) k=10;
        else
            if (n<100) k=100;
            else k=1000;
        s=n*n;
```

```
if(s%k==0)
{
    [内容被水印遮挡]
}
printf("\n The sum = %d",sum);
}
```

6. 下面程序是求[50,450]之间的能被3和5整除的数的平方和。请将程序补充完整，并给出正确结果，填入相应窗口。

```
#include <conio.h>
#include <stdio.h>
#include <math.h>
main()
{
    long sum;
    ________;
    sum=0;
    for (i=50;i<=-450;i++)
    {
        if (fmod(i,3)==0 && fmod(i,5)==0)
        {
            ________
        }
    }
    clrscr();
    printf("%ld\n",sum);
```

7. 下面的程序是求[2, 500]之间的所有的素数的个数。请将程序补充完整，并给出正确结果，填入相应窗口。

```
#include <conio.h>
#include <stdio.h>
#include <math.h>
int prime(int n)
{ int yes, i;
    if(n<=1) {return 1;}
    yes=1;
    for(i=2; i<=sqrt(n); i++)
        if(n%i==0){ yes=0; break;}
    
}
```

```
main()
{ int count=0, i;
clrscr();
for(i=2;i<=500; i++)
if(prime(i))
printf("%d\n", count);
}
```

8．下面的程序是求表达式的值：

s=1+1/3+(1*2)/(3*5)+(1*2*3)/(3*5*7)+......+(1*2*3*......*n)/(3*5*7*......*(2*n+1))请将程序补充完整，并给出当 n=20 时，程序的运行结果（按四舍五入保留10位小数）。

```
```c
#include <conio.h>
#include <stdio.h>
#include <math.h>
double fun(int n)
{
    double s, t; int i;

    __________
    t=1.0;
    for(i=1;i<=n;i++)
    { t=t*i/(2*i+1);
    __________
    }
    return s;
}
```

```
```c
main()
{
    printf("\n %12.10lf", fun(20));
}
```

9. 下面的程序是求如下表达式的值。
S=sqrt(ln(1)+ln(2)+ln(3)+......+ln(n))将程序补充完整，当 n=60时，给出程序运行结果（按四舍五入保留6位小数）。

```
#include <conio.h>
#include <stdio.h>
#include <math.h>
double fun(int n)
{
    ________________
    int i;
    for(i=1;i<=n;i++)
    s+=log(1.0*i);
    s=sqrt(s);
    return s;
}
```

![](img/609af85bac45577917bd36819bca122b_238_0.png)

```
main()
{
    clrscr();
    printf(________________);
}
```

```
```c
main()
{
    int sum=0,i;
    clrscr();
    for(i=2;i<=500; i++)
        if(prime(i)) sum+=i;
    printf("%d\n", sum);
}
```

2．下面的程序中，函数fun的功能是：根据形参m，计算下面公式的值。T=1+1/(2*3)+1/(3*4)+……+1/(m*(m+1))。请改正程序中的错误，并运行改正后的程序。当从键盘输入70时，给出程序运行的正确结果（按四舍五入保留6位小数）。

```
```c
#include <conio.h>
#include <stdio.h>

double fun(int m)
{
    double t=1.0;
    int i=2;
    for(i=2;i<=m;i++)
        t+=1.0/i*(i+1);
    return ;
}
```

```
main()
{ int m;
clrscr();
printf("\n 请输入一个整数:");
scanf("%d",&m);
printf("\n 结果是: %lf\n", fun(m));
}
```

3. 下面的程序中，函数fun的功能是：根据形参m，计算下面公式的值。 T=1/1!+1/2!+1/3!+......+1/m! 请改正程序中的错误，并运行改正后的程序。当从键盘输入10时，给出程序运行的正确结果（按四舍五入保留10位小数）。

```
#include <conio.h>
#include <stdio.h>
double fun(int m)
{ double fac, t=0.0;
int i=1, j;
for(i=1;i<=m;i++)
{ fac=1.0;
for(j=1; j<=m; j++) fac=fac*i ;
t+=1.0/fac;
}
return t;
}
```

```
```c
main()
{
    int m;
    clrscr();
    printf("\n请输入整数：");
    scanf("%d", &m);
    printf("\n结果是：%12.10lf\n", fun(m));
}
```

4. 下面的程序中，函数fun的功能是：根据形参m，计算下面公式的值。T=1+1/(1*2)+1/(2*3)+......+1/(m-1)*m 请改正程序中的错误，并运行改正后的程序。当从键盘输入70时，给出程序运行的正确结果（按四舍五入保留6位小数）。

```
#include <conio.h>
#include <stdio.h>
double fun(int m)
{ double t=1.0;
int i=2;
for(i=2;i<=m; i++)
    t+=1.0/(i*(i+1));
return ;
}
```
