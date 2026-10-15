

## 提供动态内容

- 服务器创建一个子进程并在该进程中运行由 URI 标识的程序

![](img/9bd5f6161cb6607b56d2fb964d1b8794_757_0.png)

- 子进程运行并生成动态内容。
- 服务器捕获子进程的内容并未经修改地转发给客户端

![](img/9bd5f6161cb6607b56d2fb964d1b8794_758_0.png)

- 1. 客户端如何向服务器传递程序参数？
- 2. 服务器如何将这些参数传递给子进程？
- 3. 服务器如何将与请求相关的其他信息传递给子进程？

- 4. 服务器如何捕获子进程生成的内容？

- 这些问题由通用网关接口 Common Gateway Interface (CGI) 规范解决。

![](img/9bd5f6161cb6607b56d2fb964d1b8794_761_0.png)

- **问题：**
  - 客户端如何向服务器传递参数？
- **答案：**
  - 参数附加到 URI 后面
    - `http://add.com/cgi-bin/adder?1&2`
    - `adder` 是服务器上将执行加法的 CGI 程序。
    - 参数列表以 `"?"` 开始
    - 参数之间用 `"&"` 分隔
    - 空格用 `"%20"` 表示

- **问题：**
  - 服务器如何将这些参数传递给子进程？

- **答案：**
  - 在环境变量 `QUERY_STRING` 中
    - 一个包含问号之后所有内容的字符串
    - 对于 add.com：`QUERY_STRING = "1&2"`

```c
if ((buf = getenv("QUERY_STRING")) != NULL) {
    p = strchr(buf, '/&');
    *p = '\0';
    strcpy(arg1, buf);
    strcpy(arg2, p+1);
    n1 = atoi(arg1);
    n2 = atoi(arg2);
}
```

- **问题：**
  - 服务器如何将与请求相关的其他信息传递给子进程？
- **答案：**
  - 在 CGI 规范定义的一组环境变量中。

## 一些 CGI 环境变量

- 请求特定
  - QUERY_STRING （包含 GET 参数）
  - SERVER_PORT
  - REQUEST_METHOD （GET, POST 等）
  - REMOTE_HOST （客户端域名）
  - REMOTE_ADDR （客户端 IP 地址）
  - CONTENT_TYPE （对于 POST，请求体的 MIME 类型）
  - CONTENT_LENGTH （对于 POST，字节长度）

## Tiny Web Server

- 文本中描述的 Tiny Web 服务器
  - Tiny 是一个顺序 Web 服务器。
  - 为真实浏览器提供静态和动态内容。
    - 文本文件、HTML 文件、GIF 和 JPEG 图像。
  - 226 行带注释的 C 代码。
  - 不如真正的 Web 服务器完整或健壮

```
/* Domain Name Service (DNS) host entry */
struct hostent {
    char     *h_name;        /* official name of host */
    char     **h_aliases;        /* alias list */
    int      h_addrtype;        /* host address type */
    int      h_length;          /* length of address */
    char     **h_addr_list;     /* list of addresses */
}

/* Internet address */
struct in_addr {
    unsigned int s_addr;        /* 32-bit IP address */
};

/* Generic socket address structure
(for connect, bind, and accept) */
struct sockaddr {
    unsigned short sa_family;   /* protocol family */
    char sa_data[14];           /* address data */
}
```

```
/* Internet style socket address */
struct sockaddr_in {
    /* Address family (AF_INET) */
    unsigned short sin_family;
    unsigned short sin_port;    /* Port number */
    struct in_addr sin_addr;    /* IP address */
    /* Pad to sizeof "struct sockaddr" */
    unsigned char  sin_zero[8];
};
```

## Sockets 接口概述

![](img/9bd5f6161cb6607b56d2fb964d1b8794_772_0.png)

```
struct hostent *genhostbyname(const char *name);  
struct hostent *genhostbyaddr(  
    const char *addr, int len, 0);  

/* client-side socket interface */  
int socket(int domain, int type, int protocol);  
int connect(int sockfd,  
            struct sockaddr *serv_addr,  
            int addr_len);  

/* server-side socket interface */  
int bind(int sockfd,  
         struct sockaddr *my_addr,  
         int addrlen);  
int listen(int sockfd, int backlog);  
int accept(int listenfd,  
           struct sockaddr *addr,  
           int addrlen);
```
