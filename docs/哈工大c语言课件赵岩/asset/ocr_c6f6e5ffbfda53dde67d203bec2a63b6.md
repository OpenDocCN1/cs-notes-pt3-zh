# 主调函数

# 实参

# 形参

# 被调函数

```
main()
{
    int a, b;
    a = 15;
    b = 8;
    Swap(&a, &b);
    printf("a=%d,b=%d",a,b);
}
```

```
void Swap(int *x, int *y)
{
    int temp;
    temp = *x;
    *x = *y;
    *y = temp;
}
```

a 9

b 5

&a

&b

*x

*y

temp 5