6．下列程序的功能是：求出以下分数序列的前30项之和，
2/1,3/2,5/3,8/5,13/8,21/13,……请改正程序中的错误，并运行修改后程序，
给出程序结果（按四舍五入保留6位小数）。

```
```c
#include <conio.h>
#include <stdio.h>
main()
{
  long a,b,c,k;
  double s;
  clrscr();
  s=0.0; a=2; b=1;
  for(k=1;k<=30;k++)
    s=s+a/b;
  c=a; a=a+b; b=c;
  printf("\\n 结果：%lf\\n", s);
}
```
```