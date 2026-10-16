# 6.7 循环的嵌套

例：在屏幕上打印一个8行7列的星号矩阵。

```
#include <stdio.h>
main()
{
    int i;
    for( i=0; i<7; i++ ) printf("*"); /*打印第1行星号*/
    printf("\n");
    for( i=0; i<7; i++ ) printf("*"); /*打印第2行星号*/
    printf("\n");
    .....
    for( i=0; i<7; i++ ) printf("*");/*打印第8行星号*/
}
```