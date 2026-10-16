
# 滑动窗口

- 简单的带重发的肯定确认浪费大量的带宽
- 滑动窗口(slide window)技术
  - 允许发送方在等待一个确认返回之前可以发送多个包
  - 为了区分, 需要为发出的每一个包编号
  - 发送窗口: 发送方可以一次连续发送的包的个数
  - 接收窗口: 接收方可以一次连续接收的包的个数

发送方

接收方

![](img/6da04d1fb563df13affe55d3e3f152ec_397_0.png)

![](img/6da04d1fb563df13affe55d3e3f152ec_397_1.png)

## 滑动窗口示意图

发送方

接收方

(a)初始

发送方

接收方

(b)发送0,1,2

发送方

接收方

(c)收到0,发ACK0

发送方

接收方

(d)收到ACK0,发3

发送方

接收方

(e)收到2,乱序,不发ACK2

发送方

接收方

(f)收到1,发ACK1,ACK2

发送方

接收方

(g)收到ACK1,ACK2,发4,5

## 端口、连接和端点

- TCP使用端口号来标识主机上的多个目的的进程

### TCP连接

- 用一对端点来表示

- 端点：一对整数(IP地址, 端口号), 如 (128.10.2.3, 25), 也称为套接字(Socket)

- 如两台计算机的TCP连接可以定义成 (18.26.0.36, 1069) 和 (128.10.2.3, 25)

- 多个连接可以共享一个端点, 如HTTP服务

- 与UDP的端口多路复用不同, TCP可以通过套接字对区分发送到相同端口的不同连接

## 端口、连接的例子

host A

server B

source port: x
dest. port: 23

source port:23
dest. port: x

简单的telnet应用

Web client
host C

Source IP: C
Dest IP: B
source port: y
dest. port: 80

Source IP: C
Dest IP: B
source port: x
dest. port: 80

Web client
host A

Source IP: A
Dest IP: B
source port: x
dest. port: 80

Web server B

Web服务

## TCP超时与重传

### TCP面对互联网的环境

- 报文段送到目的地的时间和确认信息返回所需的时间存在显著变化

- 如何设定确认计时器？

- 太短导致频繁的重发

  - 早期的缺省计时器为200ms, 对于卫星线路太短

- 太长则延迟太大

  - Modem缺省为3000ms, 对于LAN来说延迟太大

## TCP的自适应重发算法

### 估计平均往返时间(Round Trip Time)

- 收集每个报文段的RTT, 得到平均往返时间RTT
- 利用新的样本SampleRTT逐步修改RTT
  RTT = x*OLD_RTT + (1-x)*SampleRTT
  - x: 代表了对延迟变化的敏感程度
  - RTT=0.875*OLD_RTT+0.125*SampleRTT

### 设置超时时间

- Timeout=β*RTT，β>1，最初推荐β=2

## 快速重传—fast retransmit

- 收到一个失序的报文段，TCP立即产生一个 ACK（一个重复的ACK）。

- 重复的ACK的目的在于让对方知道收到一个失序的报文段，并告诉对方自己希望收到的序号。

- 如果是一些报文段的重新排序，则只可能产生1-2个重复的ACK。

- 若一连串收到3个或3个以上的重复ACK，就非常可能是一个报文段丢失。

- 应该重传丢失的报文段，而无需等待超时定时器溢出。

## TCP的拥塞控制

- 端对端的拥塞控制
- 通过拥塞窗口来限制主机发送到连接上的流量样本
- 任何时候主机发送的数据量≤min(CongWin, RcvWin)
- 基本策略
  - 理想情况下用尽可能快的速度发送报文段
  - 同时增加拥塞窗口的大小直到出现报文段丢失
  - 出现丢失后,减少拥塞窗口大小,正常后再重复上述过程
- 有以下几种技术
  - 慢启动slow-start
  - 拥塞避免congestion avoidance
  - 加速递减multiplicative decrease

## 慢启动slow-start

- 每次开始新的连接或拥塞之后增加流量时
  - 拥塞窗口初始为1个报文段, 1个RTT后增加为2个段; 2个RTT后增加为4个段, 等等
- 实际上并不慢
- 建议初始拥塞窗口为2个报文段

![](img/6da04d1fb563df13affe55d3e3f152ec_406_0.png)

## 加速递减multiplicative decrease

- 一旦发现丢失报文段, 立即将拥塞窗口大小减少一半(最小值为1个报文段), 同时对于保留在发送窗口的报文段, 重设计时器时限加倍

- 用来迅速而显著地减少流量

## 提高TCP的性能

① 慢启动、加速递减、拥塞避免、对延迟变化的测量、快速重传等技术结合在一起可以在不明显增加协议软件开销的情况下显著提高TCP的性能, 2-10倍

## TCP连接的建立与中止

### 三次握手 3way handshake

– 通信双方彼此之间交换三次信息

– 已经证明

- 在存在包丢失、重复和延迟的情况下，确保通信双方信息交换确定性的充要条件是三次握手！

![](img/6da04d1fb563df13affe55d3e3f152ec_411_0.png)

![](img/6da04d1fb563df13affe55d3e3f152ec_411_1.png)

① 说明
- CR建立连接的请求
- ACC同意建立连接
- REJ拒绝连接

② 目的: 不会出现过时的CR、ACC、或其他可能引起协议失败的组合,也不会无故地建立无人要求的连接

## 释放连接

### 两种方式

- 对称释放：将连接按照两个独立的单向连接来处理，要求每一方分别释放连接
- 非对称释放：一方结束后，连接即告中断。类似于打电话。但是可能导致数据丢失。

![](img/6da04d1fb563df13affe55d3e3f152ec_412_0.png)

## 对称释放的问题-两军问题

蓝军 A

蓝军 B

4.1进攻

同意

收到同意

?

B不会进攻,不知“同意”是否安全到达

A不会进攻,不知“收到同意”是否安全到达

四次握手也不行 最后发出消息的指挥官永远无法确定信息是否安全到达

> 如果连接的双方在的确信对方也准备释放连接之前都不准备断开连接,那么连接永远得不到释放！

Zhang Dongyan
TCP/IP Protocols
44

## 释放连接的设计 (1)

![](img/6da04d1fb563df13affe55d3e3f152ec_415_0.png)

![](img/6da04d1fb563df13affe55d3e3f152ec_415_1.png)

(a)正常情况

(b)最后的确认丢失

## 释放连接的设计（2）

![](img/6da04d1fb563df13affe55d3e3f152ec_416_0.png)

![](img/6da04d1fb563df13affe55d3e3f152ec_416_1.png)

![](img/6da04d1fb563df13affe55d3e3f152ec_416_2.png)

## TCP的连接建立

- 请求端(客户)发送一个SYN段指明打算连接的服务器的端口以及初始序列号(ISN, 1415531521)
- 服务器发回包含服务器初始序列号的SYN段作为应答. 同时将确认序列号设置为客户的ISN+1
- 客户必须将确认序号设置为服务器的ISN+1, 用来对服务器的SYN报文段确认

![](img/6da04d1fb563df13affe55d3e3f152ec_417_0.png)

![](img/6da04d1fb563df13affe55d3e3f152ec_419_0.png)

# Sniffer Portable - Local Ethernet (Line speed at 100 Mbps) [Sniff5: Decode, 5/178 Ethernet Frames]

| No. | Status | Source Address | Dest Address | Summary | Len (B) | Rel. Time | Delta Time |
|---|---|---|---|---|---|---|---|
| 2 |  | 202.118.236.152 | hit01.hit.edu.cn | DNS C ID=4239 OP=QUERY NAME=bbs.hit.edu.cn | 74 | 0:00:01.952 | 0:002.9 |
| 3 |  | hit01.hit.edu.cn | 202.118.236.152 | DNS C ID=4239 OP=QUERY STAT=OK NAME=bbs.hit.edu.cn | 162 | 0:00:01.952 | 0:003.2 |
| 4 |  | 202.118.236.152 | bbs.hit.edu.cn | TCP D=80 S=1451 SYN SEQ=1771264707 LEN=0 WIN=41162 | 62 | 0:00:01.954 | 0:002.9 |
| 5 |  | bbs.hit.edu.cn | 202.118.236.152 | TCP D=1451 S=80 SYN ACK=1771264708 SEQ=4041452780 WIN=60440 | 62 | 0:00:01.955 | 0:000.2 |
| 6 |  | 202.118.236.152 | bbs.hit.edu.cn | TCP D=80 S=1451 ACK=4041452780 WIN=65535 | 60 | 0:00:01.955 | 0:000.7 |
| 7 |  | 202.118.236.152 | bbs.hit.edu.cn | HTTP GET / | 488 | 0:00:01.956 | 0:000.7 |

# TCP 数据包详细信息

TCP  D=[202.118.236.152] S=[202.118.224.2] LEN=28 ID=0

- TCP: Transmission Control Protocol
  - Source port: 80 (WWW/HTTP/HTTP)
  - Destination port: 1451
  - Initial sequence number: 4041452785
  - Next expected Seq number: 4041452786
  - Acknowledgement number: 1771264708
  - Data offset: 28 bytes
  - Reserved Bits: Reserved for Future Use (Not shown in the Hex Dump)
  - Flags: 0x12
    - 0x0 = No urgent pointer
    - 0x1 = Acknowledgement
    - 0x0 = No push
    - 0x0 = No reset
    - 0x1 = SYN
    - 0x0 = No FIN
  - Window: 5840
  - Checksum: 4208 (Correct)
  - Urgent pointer: 0
  - Options follow
  - Maximum segment size = 1460
  - No-Operation
  - No-Operation
  - SACK-Permitted Option

```
00000010  00 30 00 40 71 3e 6d ab 1f ca 76 c0 42 ca 16
00000020  ec 98 00 50 01 ab e3 a5 1f 69 93 5a c4 70 76
00000030  16 ad 80 28 00 00 02 40 04 10 91 04 12 00 00
```

Expert | Decode | Matrix | Host Table | Protocol Dist. | Statistics
