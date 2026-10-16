设坐标原点在数组的第13行第39列上，数组列标表示X坐标，行标表示Y坐标。考虑屏幕的行列比例，计算函数值时X坐标与Y坐标的比例应设为2:1，即横方向的两个字符代表的数值应与竖方向一行代表的数值一样。最后，定 a = 12，程序如下：

```
```c
/* PROGRAM rose /* 本页为声明部分 */
#include <stdio.h>
#include <math.h>
#define pi 3.1415926
#define aspectratio 2
#define a 12
float t;
int x,y,i;
char grid[25][79];
```
```