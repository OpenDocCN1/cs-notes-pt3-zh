# 例7.13 从键盘上输入两个字符串，若不相等，将短的字符串连接到长字符串的末尾并输出。

```
#include<stdio.h>
#include<string.h>
main()
{int len1,len2
char s1[80],s2[80];
gets(s1);gets(s2);
if(strcmp(s1,s2)!=0)
{ if(strlen(s1)>strlen(s2)) {strcat(s1,s2);puts(s1);}
else {strcat(s2,s1);puts(s2);}
}
```

输入： you
Thank

输出： Thank you