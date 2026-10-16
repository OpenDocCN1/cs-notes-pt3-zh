# 例6.7 求斐波纳契数列：1，1，2，3，5，8…的前40个数。

```
```c
#include<math.h>
main()
{
    long int f1=1, f2=1, i;
    for(i=1;i<=20;i++)
    {
        printf("%12ld %12ld",f1,f2);
        if(fmod(i,2)==0) printf("\n");
        f1=f1+f2;
        f2=f1+f2;
    }
}
```
```

![](bbox=[0.583, 0.344, 1.0, 0.956])