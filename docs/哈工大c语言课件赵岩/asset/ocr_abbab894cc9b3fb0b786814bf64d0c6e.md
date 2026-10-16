# 文件字符串读取

```
char *fgets(char *s, int n, FILE *fp);
int fputs(const char *s, FILE *fp);
```

+   - 当读到换行、文件末尾或读满n-1个字符时返回
+   - 且在字符串末尾添加'\0'
+   - 返回值：若读入成功，则返回字符串地址，否则返回一个NULL

+   - 字符串输出到fp
+   - 返回值：若输出成功，则返回一个非负值，否则返回EOF