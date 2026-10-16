# 词法分析器的任务：
分离单词，检查词法错误

```
#include "stdio.h"
#define pai 3.14
int main()
{
    float radius = 2;
    float area;
    area=2*pai*radius;
    printf("%.2f",@area);
    return 0;
}
```

字符序列

词法分析程序

词法错误：只有一种语言不允许的字符

Token序列

```
......
<保留字， int>
<保留字， main>
<界限符， (>
<界限符， )>
<界限符， {>
<保留字， float>
<标识符， radius>
<运算符， =>
<常量， 2>
<界限符， ;>
......
```