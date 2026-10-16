# 例： 输入两个数,比较其大小，将较大的数输出。

算法分析：

+   (1) 输入两个数据a,b；
+   (2) 如果a>b 则输出a； 否则，输出b。

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