# 写文件

+   写文件从内存复制字节到当前文件位置，然后更新文件位置

```
char buf[512];
int fd;      /* file descriptor */
int nbytes;  /* number of bytes read */

/* Open the file fd ... */
/* Then write up to 512 bytes from buf to file fd */
if ((nbytes = write(fd, buf, sizeof(buf)) < 0) {
    perror("write");
    exit(1);
}
```

+   返回值表示的是从内存向文件fd实际传送的字节数量

+   nbytes < 0 表明发生错误

+   同读文件一样,不足值（short counts）是可能的，并不是错误！