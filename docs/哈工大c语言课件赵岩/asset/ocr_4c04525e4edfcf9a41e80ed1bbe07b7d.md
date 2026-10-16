# 利用数组计算Fibonacci数列

```
```c
#define YEAR_MONTH 12

int f[YEAR_MONTH+1] = {0,1,2};
int month;
for (month=3; month<=YEAR_MONTH; month++)
{
    f[month] = f[month-1] + f[month-2];
}
for (month=1; month<=YEAR_MONTH; month++)
{
    printf("%d\t", f[month]);
}
printf("\nsum = %d\n", f[YEAR_MONTH]);
```
```