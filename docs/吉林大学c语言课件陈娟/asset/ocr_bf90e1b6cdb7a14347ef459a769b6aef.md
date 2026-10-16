```
```c
(5) char *str;
    str="I am a teacher";
    // 正确，给指针变量赋值，str指向常量字符串
```
```

```
```c
(6) char str[20];
    scanf("%s",str);
    // 正确，输入字符串
```
```

```
```c
(7) char *str;
    scanf("%s",str);
    // 错误，str不指向任何变量，输入字符串无处放
```
```