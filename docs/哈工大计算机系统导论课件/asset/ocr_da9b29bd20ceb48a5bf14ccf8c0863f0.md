# 读文件

+   - 读文件从当前文件位置复制字节到内存位置，然后更新文件位置

```
char buf[512];
int fd;      /* file descriptor */
int nbytes;  /* number of bytes read */

/* Open file fd ... */
/* Then read up to 512 bytes from file fd */
if ((nbytes = read(fd, buf, sizeof(buf))) < 0) {
    perror("read");
    exit(1);
}
```

+   - 返回值表示的是实际传送的字节数量

+   - 返回类型 ssize_t 是有符号整数
+   - nbytes < 0 表示发生错误
+   - 不足值（Short counts）(nbytes < sizeof(buf)) 是可能的，不是错误！