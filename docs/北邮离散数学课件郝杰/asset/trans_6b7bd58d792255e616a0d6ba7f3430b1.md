

## Email的通信协议

- SMTP：发送/转发邮件——PUSH服务
- POP3或IMAP：从邮箱收邮件到本地计算机——PULL服务

![](img/ec5c59e5ed61c3b45834fc86d9ef22ae_231_0.png)

## SMTP [RFC 5321]

- 简单邮件传输协议，Simple Mail Transfer Protocol
- 采用C/S模式
- 传输层协议使用TCP，Server端口号是25
- 直接传输：邮件直接从发信人的服务器传输到收信人的服务器，而不由中间服务器转发
- 命令/响应方式交互（类似HTTP）
  - 命令(Command)：ASCII文本
  - 应答(Reply)：状态码和短语
- 只支持7位ASCII文本邮件
  - 格式由RFC5322确定

## SMTP交互示例

Client首先要建立到Server的TCP连接

```
S: 220 AnyMacro Email System
C: EHLO mail.bupt.edu.cn
S: 250-mx4.bupt.edu.cn
C: MAIL FROM: <chengli@bupt.edu.cn>
S: 250 Ok
C: RCPT TO: <liujy@bupt.edu.cn>
S: 250 Ok
C: RCPT TO: <noname@bupt.edu.cn>
S: 550 Recipient address rejected: User unknown in local recipient table
C: Data
S: 354 End data with <CR><LF>.<CR><LF>
C: 邮件数据（消息头+正文）
C: .
S: 250 Ok: queued as E75A2B644B
C: QUIT
S: 221 Bye
```

## SMTP 小结

- SMTP使用持久连接
- SMTP只支持传输ASCII文本消息
- SMTP服务器使用回车换行符.回车换行符(只包含". "的一行)来判断邮件结束

### 与HTTP比较：

- HTTP: pull
- SMTP: push
- 均使用持久连接
- 均采用ASCII命令/响应进行交互，响应均包含状态码

## 邮件访问协议

- 邮件访问协议：从邮件服务器收/读邮件
  - POP：Post Office Protocol [RFC 1939]
    - 对用户进行身份认证、下载邮件到用户计算机
  - IMAP：Internet Mail Access Protocol [RFC 1730]
    - 比POP功能强、复杂
    - 可以在邮件服务器上处理邮件
  - Webmail：使用浏览器读邮件

## POP3 vs. IMAP

### POP3

- 用户使用客户端程序访问邮件服务器
- 用户下载邮件时可以选择
  - 下载后从服务器删除，或
  - 在服务器上保留副本
- 服务器上一个用户只有一个文件夹：inbox
- 会话状态信息不保留

### IMAP

- 用户可以使用客户端或浏览器访问服务器
- 邮件一直保留在服务器
- 用户可以在服务器上创建并管理多个文件夹
- 用户可以只读取邮件头，或部分邮件（如文本）

示例：bupt.edu.cn的邮件服务器，可以选择使用POP3或者IMAP访问邮箱

## POP3 vs. IMAP

| 操作位置 | 操作内容 | IMAP | POP3 |
|---|---|---|---|
| 收件箱 | 阅读、标记、移动、删除邮件等 | 客户端与邮箱更新同步 | 仅客户端内 |
| 发件箱 | 保存到已发送 | 客户端与邮箱更新同步 | 仅客户端内 |
| 创建文件夹 | 新建自定义的文件夹 | 客户端与邮箱更新同步 | 仅客户端内 |
| 草稿 | 保存草稿 | 客户端与邮箱更新同步 | 仅客户端内 |
| 垃圾文件夹 | 接收误移入垃圾文件夹的邮件 | 支持 | 不支持 |
| 广告邮件 | 接收被移入广告邮件夹的邮件 | 支持 | 不支持 |

## Web mail（基于网页的邮件）

![](img/ec5c59e5ed61c3b45834fc86d9ef22ae_238_0.png)

- 用户通过浏览器访问邮件服务器
- 用户可以在服务器上创建和管理自己的文件夹

![](img/ec5c59e5ed61c3b45834fc86d9ef22ae_238_1.png)

## 邮件格式：多媒体扩展

### SMTP的缺点：

- 不能传送可执行文件或其他二进制对象
- 限于传送7位的ASCII码，不能支持其他编码和语言
- 会拒绝超过一定长度的邮件
- 某些SMTP的实现没有完全按照SMTP的因特网标准

### 通用因特网邮件扩充（MIME）

- 并未改动或取代SMTP
- 定义了传送非ASCII码的规则

## 邮件格式：多媒体扩展

- MIME: multimedia mail extension, RFC 2045, 2056
- 在邮件头增加字段，说明媒体数据的类型

MIME版本
数据编码方法
多媒体数据类型、子类型、相关参数
已编码的数据

```
From: alice@crepes.fr
To: bob@hamburger.edu
Subject: Picture of yummy crepe.
MIME-Version: 1.0
Content-Transfer-Encoding: base64
Content-Type: image/jpeg

base64 encoded data .....
.....................
......base64 encoded data
```

## MIME邮件头字段

| 消息头字段 | 含义描述 |
| --- | --- |
| MIME-Version: | 标识MIME的版本 |
| Content-Id: | 邮件消息内容的唯一标识符 |
| Content-Type: | 邮件中的数据类型 |
| Content-Transfer-Encoding: | 邮件传输的编码方式 |
| Content-Description: | 关于邮件内容的英文描述 |

## MIME支持的数据类型

| 类型 | 子类型 | 含义描述 |
|---|---|---|
| Text | Plain | 无格式文本 |
| Text | Richttext | 有简单格式的文本 |
| Image | Gif | GIF格式静态图像 |
| Image | Jpeg | JPEG格式静态图像 |
| Audio | Basic | 音频 |
| Video | Mpeg | MPEG格式视频 |
| Application | octet-stream | 字节序列 |
| Application | Postscript | PostScript 文档 |
| Message | RFC5322 | RFC 5322格式的消息 |
| Message | Partial | 部分消息（消息被拆分，以便于传输） |
| Message | External-body | 访问外部数据的机制（访问方法、URL等） |
| Multipart | Mixed | 消息的多个独立部分按顺序组织在一起 |
| Multipart | Alternative | 相同消息的另一种格式 |
| Multipart | Parallel | 消息的多个部分必须同步 |
| Multipart | Digest | 每个部分都是完整的RFC 5322消息 |

## Base64编码

- 编码，而不是加密
- 规则：将数据重新编码成7位，通常用于传送二进制文件，也用于SMTP等协议中传输用户名和密码
- 方法：把二进制代码划分为一个个24位长的单元，然后把每个24位单元划分为4个6位组。每个6位组按以下方法转换成ASCII码
- A-Z表示0-25，a-z表示26-51，0-9表示52-61，+表示62，/表示63，==表示最后一组只有8位，=表示最后一组只有16位
- Base64编码后的文字通常是这个样子：
  pGquYaZuoUmn2qxPseepc6dnoUGr3LCqv70ms

## Base64编码示例

24位二进制代码：01001001 00110001 01111001

划分为4个6位组

010010 010011 000101 111001

对应的base64编码 S T F 5

用ASCII码发送：

01010011 01010100 01000110 00110101

