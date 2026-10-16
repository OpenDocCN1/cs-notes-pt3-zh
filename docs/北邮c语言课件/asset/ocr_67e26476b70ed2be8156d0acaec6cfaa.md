# 程序：

```
#include "stdio.h"
void main()
{
    char a;
    printf("Input a lowercase letter: ");
    a=getchar();
    a = a-32;
    a='a'<=a&&a<='z'?a-32:a;
    printf("%c\n", a);
    printf("%c\n",a);
}
```

思考：如何使程序可以处理任何字符的输入。即判断输入的是小写字母，才转换成大写；如果输入的其他字符，则直接输出。