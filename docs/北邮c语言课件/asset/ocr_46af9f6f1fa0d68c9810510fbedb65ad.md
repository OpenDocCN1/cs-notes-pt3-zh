```
```c
#include "stdio.h"
main()
{
    int i,radix;
    long n;
    char a[33];
    void trans10_2_8_16(char *b,long m,int base);
    printf("\nInput radix(2,8,16):");/* 输入转换基数 */
    scanf("%d",&radix);
    printf("\nInput a positive integer:");/* 输入被转换的数 */
    scanf("%ld",&n);
    trans10_2_8_16(a,n,radix);
    for (i=strlen(a)-1;i>=0; i--)    /*逆向输出字符串*/
        printf("%c",*(a+i));        /* *(a+i) 即a[i] */
    puts("\n");
}
```
```