# 词法分析器的 工作过程：

预处理

```
#include "stdio.h"
#define pai 3.14
int main()
{
    float radius = 2;
    float area;
    area=2*pai*radius;
    printf("%.2f", @area);
    return 0;
}
```

ASCII序列

复制代码

文本替换

词法分析程序

Token序列

......
<保留字, int>
<保留字, main>
<界限符, (>
<界限符, )>
<界限符, {>
<保留字, float>
<标识符, radius>
<运算符, =>
......