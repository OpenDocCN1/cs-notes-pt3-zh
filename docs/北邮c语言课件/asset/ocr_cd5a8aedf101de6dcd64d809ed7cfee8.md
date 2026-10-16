# 程序为：

```
#define M 10
#include<stdio.h>
main()
{static int a[M]={-12,0,6,16,23,56,80,100,110,115};
int n,low,mid,high,found;
low=0;  high=M-1;  found=0;
printf("Input a number to be searched:");
scanf("%d",&n);
```