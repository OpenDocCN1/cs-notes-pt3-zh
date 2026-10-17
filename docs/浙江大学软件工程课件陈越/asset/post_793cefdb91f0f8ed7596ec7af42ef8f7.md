

## 3.5 Loops----While and For

+   * **Example 3:**

```c
#include <string.h>
/* reverse : reverse string s in place */
void reverse(char s[])
{ int c,i,j;
for(i=0,j=strlen(s)-1;i<j; i++,j--) {
c= s[i];
s[i]=s[j];
s[j]=c;
}
}
```

## 3.6 Loops---Do-while

+   - syntax:
+     do
+       statement
+     while (expression);

## Example:

```c
/* itoa: convert n to characters in s */
void itoa(int n,char s[])
{ int i,sign;
  if ((sign=n)<0 ) /*record sign */
    n=-n;
  i=0;
  do {
    s[i++]= n %10+'0'; /*get next digit */
  } while ((n/=10)>0); /*delete it */
  if( sign <0) s[i++] = '-';
  s[i]='\0';
  reverse(s);
}
```

## 3.7 Break and Continue

+   - break: exit the loop

```c
/* trim: remove trailing blanks, tabs, newlines */
int trim(char s[])
{
    int n;
    for(n=strlen(s)-1;n>=0;n--)
        if(s[n]!=' ' && s[n]!='\t' && s[n]!='\n') break;
    s[n+1]= '\0';
    return n;
}
```

*continue*: cause the next iteration to begin

```c
for(i=0;i<n;i++) {
    if(a[i]<=0) /* skip negative element */
        continue;
    /* do positive elements */
}
```

## 3.8 Goto and Labels

+   - syntax:
+     goto label_name
+     label_name: statements

Example 1:
for(...)
  for(...) {
    if(disaster)
      goto error;
  }
...
error: clean up the mess

## 3.8 Goto and Labels

+   - with goto:

```cpp
for(i=0;i<n;i++)
for(j=0;j<m;j++)
if(a[i]==b[j])
goto found;
/* didn't find any common element */
...
found:
/* got one: a[i] == b[j] */
...
```

### without goto:

```cpp
found = 0;
for(i=0;i<n && !found; i++)
for(j=0;j<m && !found; j++)
if(a[i] == b[j])
found = 1;
if (found)
/* got one: a[i] == b[j] */
...
else
/* didn't find any common element*/
...
```

## Examples:

【Example 1】把100~200之间不能被3整除的数输出。

```c
main()
{
    int n;

    for (n = 100; n <= 200; n++) {
        if (n%3 == 0)                 /* if (n%3) */
            continue;                  /* printf("%d ", n);*/
        printf("%d ", n);
    }
}
```

【Example 2】求 Sn=a+aa+aaa+…+aaa…a 值，其中 a 是一个数字。

+   - 例如：2+22+222+2222+22222（此时 n=5），n 和 a 由键盘输入。

+   - ☆ 算法分析：求解该题的关键是要求出每一个 aaa…a（共 i 个 a），i=1~n。而：第 i 个 a 与第（i-1）个 a 的关系：

+   - 若令：s（i-1）= aaa…a，则：
+   
+     s（i）= aaaa…a = s(i-1)*10+a

+   - 如：22=2*10+2，222=22*10+2，2222=222*10+2，

+   - 22222=2222*10+2

+   - ……

```c
#include <stdio.h>

main()
{
    int       a, n, i, j;
    long      s, s0;
    printf("Please enter digit number a: ");
    while ((a=getchar()) < '0' || a > '9') ;   /*输入一个数字*/
    a = a - '0';   /* 将字符a转换成数a*/
    printf("Please enter n: ");
    scanf("%d", &n);
    s = 0L;
    for (i = 1; i <= n; i++) {
        s0 = 0L;
        for (j = 1; j <= i; j++)     /* 求s0=aaa...a(i个a) */
            s0 = s0 * 10L + a;
        s += s0;   /* 累加前i个数 */
    }
    for (i = 1; i < n; i++) {   /* 打印a+aa+...+aaa...a+ */
        for (j = 1; j <= i; j++)
            putchar(a+'0');   /* 将数字a以字符形式打印出来 */
        printf("+");
    }
    for (j = 1; j <= n; j++)   /* 打印aaa...a(n个a) */
        putchar(a+'0');
    printf("=");
    printf("%ld\n", s);
}
```

Solution 2:
```c
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

+   • 【Example 3】

+   • 一个数如果恰好是它的因子之和，这个数就称为“完数”。例如：6的因子1、2、3，而6=1+2+3，因此，6是“完数”。编程找出1000之内的所有完数，并按下面格式输出其因子：

+   • 6 its factors are 1,2,3

+   • ☆ 算法分析：求解该题的关键是求出一个数的所有因子，又因为还要打印完数的因子，所以，还必须将每个因子暂时保存起来。

