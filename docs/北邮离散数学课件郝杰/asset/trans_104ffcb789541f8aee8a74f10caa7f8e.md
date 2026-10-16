

## Cookie文件内容示例

| 域名 | 路径 | 内容 | 过期时间 | 安全 |
|---|---|---|---|---|
| toms-casino.com | / | CustomerID=497793521 | 15-10-02 17:00 | 是 |
| joes-store.com | / | Cart=1-00501;1-07031;2-13721 | 11-10-02 14:22 | 否 |
| aportal.com | / | Prefs=Stk:SUNW+ORCL;Spt:Jets | 31-12-10 23:59 | 否 |
| sneaky.com | / | UserID=3627239101 | 31-12-12 23:59 | 否 |

## 代理服务器 (Proxy Server)

目的：减轻Web服务器的负担，加快访问速度

- 在浏览器程序中设置
- 通过代理访问
  - 浏览器将所有HTTP请求均发送给代理
    - 如果在代理中找到请求的对象，则由代理返回响应
    - 否则代理将请求转发给要访问的Web Server，由该Server 响应
    - 代理缓存来自Web Server的网页对象

![](img/ec5c59e5ed61c3b45834fc86d9ef22ae_218_0.png)

## Proxy(Web caching)

- 客户和原服务器之间的中转设备
- 既是客户端，又是服务器端
- 通常由ISP、公司或学校提供

- Proxy的优点
  - 缩短了网页访问的响应时间
  - 减轻了链路的负载
  - 减轻了服务器的负载

- 浏览器Caching:
  浏览器缓存访问过的网页，进一步减少网络负载

## 缓存的更新：条件GET

- 问题：如果cache中的对象过期了（不是最新版本）怎么办？

- Cache在HTTP请求中包含对象的最后更新时间：
  If-modified-since:
  <date>
  该时间包含在上次访问时Server的HTTP响应中
  Last-Modified: <date>

- Server如果没有更新对象，则返回
  HTTP/1.0 304 Not Modified

cache

server

HTTP 请求:
If-modified-since:
<date>

网页数据未修改

HTTP 响应:
HTTP/1.0
304 Not Modified

HTTP 请求:
If-modified-since:
<date>

网页数据有更新

HTTP 响应:
HTTP/1.0 200 OK
<data>

## HTTP的安全性：HTTPS [RFC 2818]

- 将HTTP与SSL（Secure Socket Layer）协议相结合
- 对HTTP消息加密、对Web服务器/客户进行身份认证
- 在不安全的网络上建立一条安全的通道，防止窃听和途中攻击（MITM, Man-in-the-middle attack）
- HTTP隧道（Tunneling）
  - 隧道：将一个协议数据封装在另一个协议内透明传输的方法
  - HTTP隧道：将SSL数据（加密方式、认证信息等）封装在HTTP消息内，代理对于消息中的数据不作处理，直接转发

## 主要内容

- 2.1 网络应用概述
- 2.2 DNS
- 2.3 WWW应用和HTTP
- 2.4 Email应用
  - 电子邮件系统的构成
  - 邮件地址和邮件格式
  - 邮件发送协议SMTP
  - 邮件访问协议POP3/IMAP
- 2.5 FTP
- 2.6 远程登录协议：Telnet
- 2.7 应用层安全隐患

## Email应用的特性

- 电子邮件
  - 两个计算机上的用户通过网络交换邮件消息（Mail Exchange）
- 异步应用，方便用户
- 提供一对多通信
- 价格低廉
- 谁提供Email服务？
  - ISP，如@163.com，@sina.com
  - 公司、学校、机构组织，如@bupt.edu.cn
  - 和其他应用一起，如@qq.com、@139.com

## 电子邮件系统的构成(1)

![](img/ec5c59e5ed61c3b45834fc86d9ef22ae_224_0.png)

## 电子邮件系统的构成(2)

主要包含：

- 用户代理(user agents, UA)
- 邮件服务器(mail servers)
- 邮件传输协议：SMTP
- 邮件访问协议：POP3或IMAP

### 用户代理

- 客户端程序
- 提供编辑、发送、显示邮件和邮件发送情况报告等功能
- 示例：Eudora, Outlook, Foxmail

### 邮件服务器

- 类似“邮局”，接收和转发电子邮件，向发信人报告邮件发送状态
- 邮箱：保存收到的邮件
- 消息队列：暂存待发邮件
- 使用SMTP协议传输邮件
- 采用C/S模式
- 可能是Server，也可能是Client

  - client: 发送邮件时
  - server: 接收邮件时

## 电子邮件的传输过程示例

1) Alice在我邮校园网内用UA（如Foxmail）编辑邮件，收件人是 bob@163.com
2) Foxmail把邮件发送到我的邮件服务器，邮件被放入消息队列
3) 我邮的邮件服务器建立到163.com邮件服务器的TCP连接

4) 我邮的邮件服务器把邮件转发给pop.163.com
5) 163邮件服务器把邮件保存到Bob的邮箱
6) Bob使用UA（如outlook）下载和查看邮件

![](img/ec5c59e5ed61c3b45834fc86d9ef22ae_226_0.png)

## 电子邮件地址

- 电子邮件用户必须有一个电子邮件地址
  - 许多网站提供免费电子邮件服务，需要的话可到这些网站上申请一个邮箱（电子邮件地址）。
- 电子邮件地址由两部分组成：
  - 用户名
  - 邮箱所在的邮件服务器的主机域名
  - 全球唯一性
- 用户名和邮件服务器域名之间用“@”隔开
  - 用户名@邮件服务器域名
  - 例如：
    - liujy@bupt.edu.cn

## 传统信件 vs. Email

Behrouz Forouzan
De Anza College
Cupertino, CA 96014
Sophia Fegan
Com-Net
Cupertino, CA 95014

Mail From: forouzan@deanza.edu
RCPT To: fegan@comnet.com

Sophia Fegan
Com-Net
Cupertino, CA 95014
Jan. 5, 2003
Subject: Network

Dear Mrs. Fegan:
We want to inform you that our network is working properly after the last repair.

Yours truly,
Behrouz Forouzan

From: Behrouz Forouzan
To: Sophia Fegan
Date: 1/5/03
Subject: Network

Dear Mrs. Fegan:
We want to inform you that our network is working properly after the last repair.

Yours truly,
Behrouz Forouzan

Envelope

Header

Body

Message

## 邮件消息格式(RFC5322)

```
Date: Tue, 8 Mar 2011 13:15:53 +0800
From: "chengli" chengli@bupt.edu.cn
To: "Alice" <alice@example.com.cn>
Subject: Test
Message-ID: <201103081315536592346@bupt.edu.cn>

This is test message...
```

邮件头

空行

正文

只支持ASCII文本邮件！

## 主要的邮件头

| 邮件头字段分类 | 字段 | 含义描述 |
|---|---|---|
| 发信人相关字段 | From: | 建立邮件的用户Email地址 |
|  | Sender: | 发送邮件的用户Email地址 |
|  | Reply-to: | 回邮地址 |
| 收信地址相关字段 | To: | 一个或多个收信人地址 |
|  | Cc: | 抄送地址 |
|  | Bcc: | 暗送地址 |
| 发信时间 | Date: | 邮件发送的日期和时间 |
| 标识字段 | Message-Id: | 邮件的唯一标识 |
|  | References: | 其他相关标识 |
| 信息字段 | Subject: | 邮件摘要 |
|  | Keywords: | 发信人设置的关键字 |
| 跟踪字段 | Received: | 邮件所经过的邮件服务器列表 |
|  | Return-Path: | 回邮路径 |


