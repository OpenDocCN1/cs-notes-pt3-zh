# 程序如下：

```
#include <stdio.h>
main()
{int i, flag;
    int compstr(char, char );
    char str1[80], str2[80];
    gets(str1);    gets(str2);
    i=0;
    do
    { flag=compstr(str1[i], str2[i]); /*数组元素作实参*/
      i++;
    }while((str1[i]!='\0')&&(str2[i]!='\0')&&(flag==0));
                /*只要有一个字符串到了末尾比较结束*/
```