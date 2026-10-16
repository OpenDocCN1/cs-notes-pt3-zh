# 例7.11 字符串输出示例

```
#include<stdio.h>
main()
{ static char str[20]=" How do you do ?";
    int k;
    printf(" %s",str);                /*输出str中的字符串*/
    for (k=0;str[k]!='\0';k++)
        printf(" %c",str[k]);   /*一个一个地输出字符*/
}
```

输出结果为：How do you do ? How do you do ?

使用printf() 函数的"%s"格式符来输出字符串，从数组的第一个字符开始逐个输出，直到遇到第一个'\0'为止。

使用" %c" 格式时，用循环实现每个元素的输出。