# # 第八章 指针和引用

```
例：#include<iostream.h>
void main()
{int array[5];
int * pArray=array;
for(int i=0;i<5;i++)
{array[i]=i;
cout<<pArray[i]<<" "
<< array[i] <<endl;}
}
```

此程序的运行结果为：
0 0
1 1
2 2
3 3
4 4