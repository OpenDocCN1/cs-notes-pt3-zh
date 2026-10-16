# 打开文件

+   - pathname是文件路径。可以是绝对或相对路径
+   - flags是打开方式，常用为O_RDONLY、O_WRONLY、O_RI 及O_TEXT、O_BINARY的或运算
+   - 返回值为文件描述符（File Descriptor）也叫文件句柄（File Handle），留待以后使用。如果打开失败，返回值为-1

```
1 int open(const char *pathname, int flags);
2 int fd = open("C:\\AUTOEXEC.BAT",
3             O_RDWR | O_CREAT | O_TEXT );
```