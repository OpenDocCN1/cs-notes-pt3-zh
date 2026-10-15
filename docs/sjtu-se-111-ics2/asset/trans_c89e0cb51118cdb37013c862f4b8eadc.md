

## 查询 DNS 的程序

```c
int main(int argc, char **argv) { /* argv[1] is a domain name */
    char *pp;                         /* or dotted decimal IP addr */
    struct in_addr addr;
    struct hostent *hostp;

    if (inet_aton(argv[1], &addr) != 0)
        hostp = gethostbyaddr((const char *)&addr, sizeof(addr),
                              AF_INET);
    else
        hostp = gethostbyname(argv[1]);
    printf("official hostname: %s\n", hostp->h_name);

    for (pp = hostp->h_aliases; *pp != NULL; pp++)
        printf("alias: %s\n", *pp);

    for (pp = hostp->h_addr_list; *pp != NULL; pp++) {
        addr.s_addr = *((unsigned int *)*pp);
        printf("address: %s\n", inet_ntoa(addr));
    }
}
```

## 使用 DNS 程序

```text
$ ./dns ipads.se.sjtu.edu.cn
official hostname: ipads.se.sjtu.edu.cn
address: 202.120.40.188

$ ./dns baidu.com
official hostname: baidu.com
address: 123.125.114.144
address: 220.181.111.85
address: 220.181.111.86
```

## Internet 连接

- 客户端和服务器通过发送连接的字节流进行通信
  - 点对点、全双工、可靠
- 套接字是连接的一个端点
  - 套接字地址是 IP 地址:端口 对

## Internet 连接

- 端口是一个 16 位整数，用于标识一个进程：
  - 临时端口：客户端发起连接请求时自动分配
  - 众所周知端口：与服务器提供的某项服务相关联（例如，端口 80 与 Web 服务器相关联）

## Internet 连接

- 连接由其端点的套接字地址唯一标识（*套接字对*）
  - `(cliaddr:cliport, servaddr:servport)`

## 综合起来：
Internet 连接的解剖结构

![](img/9bd5f6161cb6607b56d2fb964d1b8794_701_0.png)

## 网络编程

## 大纲

- Sockets 接口
  - 函数
  - Echo 客户端和服务器
- 建议阅读：
  - 11.4

## 客户端-服务器事务

![](img/9bd5f6161cb6607b56d2fb964d1b8794_704_0.png)

注意：客户端和服务器是运行在主机上的进程（可以是相同或不同的主机）。

## Internet 连接

- 客户端和服务器通过发送连接的字节流进行通信
  - 点对点、全双工、可靠
- 套接字是连接的一个端点
  - 套接字地址是 IP 地址:端口 对

## 综合起来：
Internet 连接的解剖结构

![](img/9bd5f6161cb6607b56d2fb964d1b8794_706_0.png)

## 客户端

- 客户端程序示例
  - Web 浏览器、ftp、telnet、ssh
- 客户端如何找到服务器？
  - 服务器进程的地址有两个部分：
    IP-address:port
  - IP 地址是一个唯一的 32 位正整数，用于标识主机（适配器）。
    - 点分十进制形式：0x8002C2F2 = 128.2.194.242
  - 端口是与该机器上的服务（从而是服务器进程）相关联的 16 位正整数

## 服务器

- 服务器是长期运行的进程（守护进程）
  - 通常在启动时由 init 进程（进程 1）创建
  - 持续运行直到机器关闭
- 运行服务器进程的机器通常也被称为“服务器”。

## 示例：Echo 客户端和服务器

### 在客户端

### 在服务器

```
server> ./echoserveri 15213
```

```
client> echoclient greatwhite.ics.cs.cmu.edu 15213
```

```
server connected to BRYANT-TP4.VLSI.CS.CMU.EDU (128.2.213.29)
```

```
type: hello there
```

```
server received 12 bytes
```

```
echo: HELLO THERE
type: ^D
```

```
Connection closed
```

## Berkeley Sockets 接口

- 创建于 80 年代初，作为包含早期 Internet 协议的原始 Berkeley Unix 发行版的一部分
- 为网络提供用户级接口
- 所有 Internet 应用的基础
- 基于客户端/服务器编程模型

