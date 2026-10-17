# 例题 1

```
```c
main()
{
    char *cp1, *cp2;

    cp1 = "12345";
    cp2 = "abcdefghij";
    strcpy(cp1,cp2);
    printf("cp1 = %s\ncp2 = %s\n", cp1, cp2);
}
```
```

在某些系统上的运行结果是：

cp1 = abcdefghij
cp2 = ghij

为什么cp2所指的串被修改了？