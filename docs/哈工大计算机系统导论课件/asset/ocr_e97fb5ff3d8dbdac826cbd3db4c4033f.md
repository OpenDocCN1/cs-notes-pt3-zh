# 链接符号类型举例

```
main.c
int buf[2] = {1, 2};
void swap();

int main()
{
swap();
return 0;
}
```

```
swap.c
extern int buf[];
int *bufp0 = &buf[0];
static int *bufp1;
void swap()
{
int temp;
bufp1 = &buf[1];
temp = *bufp0;
*bufp0 = *bufp1;
*bufp1 = temp;
}
```

你能说出哪些是全局符号？哪些是外部符号？哪些是局部符号？