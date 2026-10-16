# 数组和指针的区别

+   - 数组名是地址常量
+   - 字符指针是变量

```
1  char *pstr = "hello";  = const char *p;
2  /*内容不能更改*/

4  char astr[] = "hello";  = char const *p;
5  /*地址不能更改*/
```