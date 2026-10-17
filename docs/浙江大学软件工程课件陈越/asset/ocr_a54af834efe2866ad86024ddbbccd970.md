```
Solution 2:
#include <stdio.h>
main()
{
    int   a, n, i, j;
    long  s, s0;
    printf("Please enter digit number a: ");
    while ((a=getchar()) < '0' || a > '9') ;   /*输入一个数字*/
    a = a - '0';   /* 将字符a转换成数a */
    printf("Please enter n: ");
    scanf("%d", &n);
    s = s0 = a;
    for (i = 2; i <= n; i++) {
        s0 = s0 * 10L + a;   /* 利用i-1个a计算i个a */
        s += s0;   /* 累加前i个数 */
    }
    for (i = 1; i < n; i++) {
        for (j = 1; j <= i; j++)
            putchar(a+'0');/* 将数字a以字符形式打印出来 */
        printf("+");
    }
    for (j = 1; j <= n; j++)
        putchar(a+'0');   /* 打印aaa...a(n个a) */
    printf("=");
    printf("%ld\n", s);
}
```