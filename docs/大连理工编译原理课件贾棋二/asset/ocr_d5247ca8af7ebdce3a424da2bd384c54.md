# 例 题 3

```
main()
{ func(); printf("Return from func\n"); }
```

```
func()
{ char s[4];
strcpy(s,"12345678"); printf("%s\n",s); }
```

在X86/Linux操作系统上的运行结果如下：

12345678
Return from func
Segmentation fault (core dumped)