# scanf函数

```
1  char str[10];
2  scanf("\%s", str);
```

+   - scanf不能读入带空格的字符串，gets()可以。
+   - gets和scanf用法都不安全。
+   - 当用户的输入多于10个（含10个），str数组将越界
+   - scanf被公认为最易遭到黑客攻击的函数之一