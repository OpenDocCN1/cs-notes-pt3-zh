
## On Short Counts 不足值

+   ■ 出现“不足值”的几种情况：

+   ▪ Encountering (end-of-file) EOF on reads 读时遇到EOF

+   ▪ Reading text lines from a terminal 从终端读文本行

+   ▪ Reading and writing network sockets 读写网络套接字

+   ■ 以下几种情况不会出现“不足值”：

+   ▪ 读磁盘文件 (除了 EOF)

+   ▪ 写磁盘文件

+   ■ 最好的解决办法就是一直允许不足值，反复处理不足值

> Bryant and O'Hallaron, Computer Systems: A Programmer’s Perspective, Third Edition

## 主要内容

+   - Unix I/O
+   - 用RIO包健壮地读写
+   - 读取文件元数据，共享和重定位
+   - 标准I/O
+   - 结束语

## RIO包

RIO 是一个封装体，在像网络程序这样容易出现不足值的应用中，提供 了方便、健壮和高效的I/O

RIO 提供两类不同的函数

+   无缓冲的输入输出函数 Unbuffered input and output of binary data
+   - rio_readn 和 rio_writen

+   带缓冲的输入函数 Buffered input of text lines and binary data
+   - rio_readlineb 和 rio_readnb
+   - 带缓冲的 RIO 输入函数是线性安全的，它在同一个描述符上可以被交错地调用

> 下载地址： http://csapp.cs.cmu.edu/3e/code.html
> → src/csapp.c and include/csapp.h

## RIO的无缓冲的输入输出函数

+   - 使用与 Unix read 和 write 相同的接口
+   - 对于在网络套接字上传输数据特别有用

```
#include "csapp.h"

ssize_t rio_readn(int fd, void *usrbuf, size_t n);
ssize_t rio_writen(int fd, void *usrbuf, size_t n);

Return: num. bytes transferred if OK, 0 on EOF (rio_readn only), -1 on error
```

+   - **rio_readn** 在遇到 EOF时只能返回一个不足值
+     - 只有当确定读取字节数时才使用它
+   - **rio_writen** 绝不会返回不足值
+   - 对同一个描述符，可以任意交错地调用**rio_readn** 和 **rio_writen**

## rio_readn函数

```
/*
 * rio_readn - Robustly read n bytes (unbuffered)
 */
ssize_t rio_readn(int fd, void *usrbuf, size_t n)
{
    size_t nleft = n;
    ssize_t nread;
    char *bufp = usrbuf;

    while (nleft > 0) {
        if ((nread = read(fd, bufp, nleft)) < 0) {
            if (errno == EINTR)  /* Interrupted by sig handler return */
                nread = 0;       /* and call read() again */
            else
                return -1;       /* errno set by read() */
        }
        else if (nread == 0)
            break;               /* EOF */
        nleft -= nread;
        bufp += nread;
    }
    return (n - nleft);      /* Return >= 0 */
}
```

## RIO的带缓冲的输入函数

+   高效地从内部内存缓冲区中缓存的文件中读取文本行和二进制数据

```
#include "csapp.h"

void rio_readinitb(rio_t *rp, int fd);

ssize_t rio_readlineb(rio_t *rp, void *usrbuf, size_t maxlen);
ssize_t rio_readnb(rio_t *rp, void *usrbuf, size_t n);
```

Return: num. bytes read if OK, 0 on EOF, -1 on error

+   rio_readlineb 从文件fd中读取最大长度文本行，并存储在usrbuf

+   对于从网络套接字上读取文本行特别有用

+   停止条件

+   已经读了最大字节数

+   遇到EOF

+   遇到新行符 ('\n')

## RIO的带缓冲的输入函数

```
#include "csapp.h"

void rio_readinitb(rio_t *rp, int fd);

ssize_t rio_readlineb(rio_t *rp, void *usrbuf, size_t maxlen);
ssize_t rio_readnb(rio_t *rp, void *usrbuf, size_t n);

Return: num. bytes read if OK, 0 on EOF, -1 on error
```

+   - **rio_readnb** 从文件 fd 最多读n个字节
+   - 停止条件
+     - 已读最大字节数 **maxlen**
+     - 遇到EOF
+   - 同一个描述符对 **rio_readlineb** 和 **rio_readnb** 的调用可以任意交叉进行
+     - **警告: 不要和 rio_readn 函数交叉使用**

## 带缓冲I/O的应用

+   - 读文件

+   - 文件关联的缓冲区来保存从文件中读取，但是还未被用户代码读取的字节

![](img/7ab811dea080313a753fa0ae68528fa9_1611_0.png)

+   - Unix 文件分层：

![](img/7ab811dea080313a753fa0ae68528fa9_1611_1.png)

## 带缓存的IO：声明

+   结构中包含所有信息

![](img/7ab811dea080313a753fa0ae68528fa9_1612_0.png)

```
typedef struct {
    int rio_fd;                 /* descriptor for this internal buf */
    int rio_cnt;                /* unread bytes in internal buf */
    char *rio_bufptr;           /* next unread byte in internal buf */
    char rio_buf[RIO_BUFSIZE];  /* internal buffer */
} rio_t;
```

## RIO函数示例

+   从标准输入复制一个文本文件到标准输出

```
#include "csapp.h"

int main(int argc, char **argv)
{
    int n;
    rio_t rio;
    char buf[MAXLINE];

    Rio_readinitb(&rio, STDIN_FILENO);
    while((n = Rio_readlineb(&rio, buf, MAXLINE)) != 0)
        Rio_writen(STDOUT_FILENO, buf, n);
    exit(0);
}
cpfile.c
```

## 主要内容

+   - Unix I/O
+   - 用RIO包健壮地读写
+   - 读取文件元数据，共享和重定位
+   - 标准I/O
+   - 结束语

## 读取文件元数据

+   - 元数据(Metadata) 是关于文件的信息
+   - 每个文件的元数据都有内核来保存
+     - 用户通过调用 stat和fstat 函数访问元数据

```
/* Metadata returned by the stat and fstat functions */
struct stat {
    dev_t        st_dev;      /* Device */
    ino_t        st_ino;      /* inode */
    mode_t       st_mode;     /* Protection and file type */
    nlink_t      st_nlink;    /* Number of hard links */
    uid_t        st_uid;      /* User ID of owner */
    gid_t        st_gid;      /* Group ID of owner */
    dev_t        st_rdev;     /* Device type (if inode device) */
    off_t        st_size;     /* Total size, in bytes */
    unsigned long st_blksize; /* Blocksize for filesystem I/O */
    unsigned long st_blocks;  /* Number of blocks allocated */
    time_t       st_atime;    /* Time of last access */
    time_t       st_mtime;    /* Time of last modification */
    time_t       st_ctime;    /* Time of last change */
};
```
