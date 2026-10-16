# 例8.10 有若干本书，将书名按字典顺序排序

```
#include<stdio.h>
#include<string.h>
main()
{ char *bname[]={"Programming in ANSI C","BASIC","Visual C++ 6.0 Programming ","TRUBO C 2.0"};
int i,m;
void sort(char *name[],int);
m=sizeof(bname)/sizeof(char *); /*字符串个数*/
sort(bname,m);        /* 排序，改变指针的连接关系*/
printf("\n");
for (i=0;i<m;i++)     /*输出排序结果*/
printf("%8s",bname[i]);
}
```