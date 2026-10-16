```
void swap()
{ int t;
    t = a; a = b; b = t;
    printf("swap:a=%d, b=%d\n", a, b);
}
main()
{
    printf(" Enter a, b:");
    scanf("%d,%d", &a, &b);
    swap();
    printf ("main:a=%d, b=%d", a, b);
}
```

运行结果
程序在编译时，屏幕将提示有错误：
Undefine symbol ‘a’
Undefine symbol ‘b’

int a, b;