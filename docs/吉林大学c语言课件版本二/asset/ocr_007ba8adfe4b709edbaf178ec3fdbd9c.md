```
/* A */
#include <stdio.h>
int i;main (){i=25+38;printf(“25+38=%d”,i);}
```

```
/* B */
#include <stdio.h>
int i;main ()
{
i = 25+38;
printf (“25+38=%d” , i );
;}
```

```
/* C */
#include <stdio.h>
int i; /* 声明整型变量i */
int main (void) { /* 主函数 */
i = 25+38; /* 求和运算 */
printf (“25+38=%d” , i); /* 打印 */
}
```