
## SMTP协议: RFC 2821

使用TCP进行email消息的可靠传输

端口 25

传输过程的三个阶段

- 握手
- 消息的传输
- 关闭

命令/响应交互模式

- 命令(command): ASCII文本
- 响应(response): 状态代码和语句

Email消息只能包含7位ASCII码

## Email应用示例

![](img/b7a9324545f24cd4f1f7132598005229_78_0.png)

## SMTP交互示例

```
S: 220 hamburger.edu
C: HELO crepes.fr
S: 250 Hello crepes.fr, pleased to meet you
C: MAIL FROM: <alice@crepes.fr>
S: 250 alice@crepes.fr... Sender ok
C: RCPT TO: <bob@hamburger.edu>
S: 250 bob@hamburger.edu ... Recipient ok
C: DATA
S: 354 Enter mail, end with "." on a line by itself
C: Do you like ketchup?
C: How about pickles?
C: .
S: 250 Message accepted for delivery
C: QUIT
S: 221 hamburger.edu closing connection
```

## 动手尝试SMTP交互

- telnet servername 25
- 服务器返回代码220
- 输入以下命令与SMTP服务器交互
  - HELO
  - MAIL FROM
  - RCPT TO
  - DATA
  - QUIT

![](img/b7a9324545f24cd4f1f7132598005229_80_0.png)

## SMTP协议

- 使用持久性连接
- 要求消息必须由7位ASCII码构成
- SMTP服务器利用`CRLF.CRLF`确定消息的结束。

与 HTTP 对比：

- HTTP: 拉式(pull)
- SMTP: 推式(push)
- 都使用命令/响应交互模式
- 命令和状态代码都是ASCII码
- HTTP: 每个对象封装在独立的响应消息中
- SMTP: 多个对象在由多个部分构成的消息中发送

Email作为互联网上的古老应用，从出现至今经过了什么样的演变过程？

站在今天的角度看，Email应用有哪些缺点和不足？请查阅资料，给出你的见解。

![](img/b7a9324545f24cd4f1f7132598005229_82_0.png)

## 哈尔滨工业大学

HARBIN INSTITUTE OF TECHNOLOGY

立足航天，服务国防，面向国民经济主战场

## 谢谢！

## 计算机网络之网尽其用

主讲人：聂兰顺

## Email消息格式与POP3协议

## Email消息格式

- SMTP：email消息的传输/交换协议
- RFC 822：文本消息格式标准

- 头部行(header)
  - To
  - From
  - Subject
- 消息体(body)
  - 消息本身
  - 只能是ASCII字符

与SMTP命令不同

![](img/b7a9324545f24cd4f1f7132598005229_86_0.png)

## 邮件访问协议

![](img/b7a9324545f24cd4f1f7132598005229_88_0.png)

### 邮件访问协议：从服务器获取邮件

- POP: Post Office Protocol [RFC 1939]
  - 认证/授权(客户端←→服务器)和下载
- IMAP: Internet Mail Access Protocol [RFC 1730]
  - 更多功能
  - 更加复杂
  - 能够操纵服务器上存储的消息
- HTTP: 163, QQ Mail等。

## POP协议

- 认证过程
  - 客户端命令
    - User：声明用户名
    - Pass：声明密码
  - 服务器响应
    - +OK
    - -ERR
- 事务阶段
  - List：列出消息数量
  - Retr：用编号获取消息
  - Dele：删除消息
  - Quit

```
S: +OK POP3 server ready
C: user bob
S: +OK
C: pass hungry
S: +OK user successfully logged on

C: list
S: 1 498
S: 2 912
S: .
C: retr 1
S: <message 1 contents>
S: .
C: dele 1
C: retr 2
S: <message 2 contents>
S: .
C: dele 2
C: quit
S: +OK POP3 server signing off
```

## POP协议

- “下载并删除”模式
  - 用户如果换了客户端软件，无法重读该邮件
- “下载并保持”模式：不同客户端都可以保留消息的拷贝
- POP3是无状态的

## IMAP协议

- 所有消息统一保存在一个地方：服务器
- 允许用户利用文件夹组织消息
- IMAP支持跨会话(Session)的用户状态:
  - 文件夹的名字
  - 文件夹与消息ID之间的映射等

## 课后练习

请查阅资料，比较IMAP与POP3的不同，并调研主流Email服务对IMAP协议的支持情况。

![](img/b7a9324545f24cd4f1f7132598005229_92_0.png)

## 哈尔滨工业大学

HARBIN INSTITUTE OF TECHNOLOGY

立足航天，服务国防，面向国民经济主战场

## 谢谢！

## 计算机网络之网尽其用

主讲人：聂兰顺

## DNS概述

## DNS: Domain Name System

- Internet上主机/路由器的识别问题
  - IP地址
  - 域名：`www.hit.edu.cn`

问题：域名和IP地址之间如何映射？

- 域名解析系统DNS
  - 多层命名服务器构成的分布式数据库
  - 应用层协议：完成名字的解析
    - Internet核心功能，用应用层协议实现
    - 网络边界复杂

![](img/b7a9324545f24cd4f1f7132598005229_96_0.png)

## DNS

### DNS服务

- 域名向IP地址的翻译
- 主机别名
- 邮件服务器别名
- 负载均衡：Web服务器

### 问题：为什么不使用集中式的DNS？

- 单点失败问题
- 流量问题
- 距离问题
- 维护性问题

![](img/b7a9324545f24cd4f1f7132598005229_97_0.png)

## 分布式层次式数据库

![](img/b7a9324545f24cd4f1f7132598005229_98_0.png)

客户端想要查询 `www.amazon.com` 的IP

- 客户端查询根服务器，找到com域名解析服务器
- 客户端查询com域名解析服务器，找到amazon.com域名解析服务器
- 客户端查询amazon.com域名解析服务器，获得www.amazon.com的IP地址

## DNS根域名服务器

- 本地域名解析服务器无法解析域名时，访问根域名服务器
- 根域名服务器
  - 如果不知道映射，访问权威域名服务器
  - 获得映射
  - 向本地域名服务器返回映射

![](img/b7a9324545f24cd4f1f7132598005229_99_0.png)

全球有13个根域名服务器

## TLD和权威域名解析服务器

- 顶级域名服务器(TLD, top-level domain): 负责com、org、net、edu等顶级域名和国家顶级域名，例如cn、uk、fr等
  - Network Solutions维护com顶级域名服务器
  - Educause维护edu顶级域名服务器
- 权威(Authoritative)域名服务器: 组织的域名解析服务器，提供组织内部服务器的解析服务
  - 组织负责维护
  - 服务提供商负责维护
