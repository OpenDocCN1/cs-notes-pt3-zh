# 汉字用两位ASCII存储

+   - 汉字文本测试程序

```
#include<stdio.h>
#include<string.h>
int main(void)
{
    char s[]="我";
    unsigned char *p=(unsigned char *)s;
    printf("%d\n",strlen(s));
    printf("%X\n",*p);
    printf("%X\n",*(p+1));
    system("pause");
    return 0;
}
```

输出结果：
2
CE
D2
Press any key to continue