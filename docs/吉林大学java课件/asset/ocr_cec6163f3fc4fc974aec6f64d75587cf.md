# ◆String类

```
String s1 = "hello";
String s2 = "world";
String s3 = "hello";
...
```

Code

Constant
常量池

"hello"
"world"
...

s1
s2
s3
...

Stack
栈

用引号创建的对象" hello"和" world"是存储在常量池当中的，s1和s3指向的是同一块内存区域。因此，当我们用等号比较时，可以得到true的结果。