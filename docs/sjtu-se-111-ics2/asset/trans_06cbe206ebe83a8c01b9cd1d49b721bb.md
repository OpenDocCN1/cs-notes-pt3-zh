

## 全球 IP 互联网

- 基于 TCP/IP 协议族。
  - UDP（不可靠数据报协议）
    - 使用 IP 为进程间提供不可靠的数据报传输。
  - TCP（传输控制协议）
    - 使用 IP 为进程间提供可靠的字节流，例如文件。
- 通过 Unix 文件 I/O 和 Berkeley sockets 接口的函数混合访问。

## 互联网应用的硬件和软件组织

![](img/9bd5f6161cb6607b56d2fb964d1b8794_684_0.png)

## 程序员视角的互联网

- 主机被映射到一组 32 位 **IP 地址**。
  - `202.120.40.188`（ICS 服务器）
- IP 地址集合被映射到一组称为互联网 **域名** 的标识符。
  - `202.120.40.188` 被映射到 `ipads.se.sjtu.edu.cn`。
- 一个主机上的进程通过 **连接** 与另一个主机上的进程通信。

## 点分十进制表示法

- 按惯例，32 位 IP 地址中的每个字节都由其十进制值表示并用句点分隔。
  - IP 地址 `0xca7828bc` = `202.120.40.188`。

## 点分十进制表示法

- 用于在二进制 IP 地址和点分十进制字符串之间转换的函数：
  - **inet_aton**：将点分十进制字符串转换为网络字节序的 IP 地址。
  - **inet_ntoa**：将网络字节序的 IP 地址转换为对应的点分十进制字符串。
  - “n” 表示网络表示。“a” 表示应用表示。

## IP 地址

- 32 位 IP 地址存储在 IP 地址结构体中。
  - IP 地址始终以网络字节序（大端字节序）存储在内存中。

```c
/* Internet address structure */
struct in_addr {
    unsigned int s_addr; /* network byte order (big-endian) */
};
```

## 有用的网络字节序转换函数

- **htonl**：将 `uint32_t` 从主机字节序转换为网络字节序。
- **htons**：将 `uint16_t` 从主机字节序转换为网络字节序。
- **ntohl**：将 `uint32_t` 从网络字节序转换为主机字节序。
- **ntohs**：将 `uint16_t` 从网络字节序转换为主机字节序。

## 互联网域名

![](img/9bd5f6161cb6607b56d2fb964d1b8794_689_0.png)

## 域名系统（DNS）

- 互联网在名为 DNS 的庞大分布式数据库中维护 IP 地址和域名之间的映射。
- 概念上，我们可以将 DNS 数据库视为数百万个主机条目结构。

## 域名系统（DNS）

```c
/* DNS host entry structure */
struct hostent {
    /* official domain name of host */
    char  *h_name;
    /* null-terminated array of domain names */
    char  **h_aliases;
    /* host address type (AF_INET) */
    int   h_addrtype;
    /* length of an address, in bytes */
    int   h_length;
    /* null-terminated array of in_addr structs */
    char  **h_addr_list;
};
```

## DNS 主机条目的属性

- 每个主机条目都是域名和 IP 地址的等价类。
- 每个主机都有一个本地定义的域名 `localhost`，它始终映射到回环地址 `127.0.0.1`。

## DNS 主机条目的属性

- 可能存在不同种类的映射：
  - **1-1**：域名与 IP 地址之间的映射：
    - `ipads.se.sjtu.edu.cn` 映射到 `202.120.40.188`。
  - **M-1**：多个域名映射到同一个 IP 地址：
    - `google.com.cn` 和 `google.cn` 都映射到 `74.125.128.160`。

## DNS 主机条目的属性

- 可能存在不同种类的映射：
  - **M-N**：多个域名映射到多个 IP 地址：
    - `baidu.com` 和 `baidu.com.cn` 映射到三个不同的 IP 地址。
  - **1-?**：某些有效域名不映射到任何 IP 地址：
    - `ics.se.sjtu.edu.cn`。

## 域名系统（DNS）

- 用于从 DNS 检索主机条目的函数：
  - **gethostbyname**：查询键为 DNS 域名。
  - **gethostbyaddr**：查询键为 IP 地址。

