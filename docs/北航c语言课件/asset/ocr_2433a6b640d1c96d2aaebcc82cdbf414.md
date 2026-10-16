# 四、函数的分类

1. 从函数的参数形式看，函数可分为两类：

+   ①无参函数；　　②有参函数

```
有参函数例：（输出两数中大者）
#include <stdio.h>
int max( int x, int y ); //定义函数原形
void main( )
{
    int num1,num2,a;
    scanf("%d,%d",&num1,&num2);
    a = max(num1,num2);
    printf("max=%d",a);
}
```

```
int max( int x, int y )
{
    int z;
    if(x>y) z=x;
    else z=y;
    return z;
}
```