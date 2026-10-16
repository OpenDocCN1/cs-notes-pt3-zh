
## 快速重传算法

```
event: ACK received, with ACK field value of y
    if (y > SendBase) {
        SendBase = y
        if (there are currently not-yet-acknowledged segments)
            start timer
    }
    else {
        increment count of dup ACKs received for y
        if (count of dup ACKs received for y = 3) {
            resend segment with sequence number y
        }
    }
```

a duplicate ACK for already ACKed segment

fast retransmit

## 哈尔滨工业大学

HARBIN INSTITUTE OF TECHNOLOGY

立足航天，服务国防，面向国民经济主战场

## 谢谢！

## 计算机网络之探幽索隐

主讲人：聂兰顺

## TCP流量控制

+ 接收方为TCP连接分配buffer

![](img/b7a9324545f24cd4f1f7132598005229_246_0.png)

flow control
发送方不会传输的太多、太快以至于淹没接收方
（buffer溢出）

+ 速度匹配机制

+ 上层应用可能处理 buffer中数据的速度较慢

## TCP流量控制

![](img/b7a9324545f24cd4f1f7132598005229_247_0.png)

(假设TCP)receiver丢弃乱序的 segments)

+ - Buffer中的可用空间(spare room)
+ = RcvWindow
+ = RcvBuffer - [LastByteRcvd - LastByteRead]

+ - Receiver通过在Segment的头部字段将 RcvWindow 告诉Sender

+ - Sender限制自己已经发送的但还未收到ACK的数据不超过接收方的空闲 RcvWindow 尺寸

+ - Receiver告知Sender RcvWindow=0,会出现什么情况？

![](img/b7a9324545f24cd4f1f7132598005229_247_1.png)

## 哈尔滨工业大学

HARBIN INSTITUTE OF TECHNOLOGY

立足航天，服务国防，面向国民经济主战场

## 谢谢！

## 计算机网络之探幽索隐

主讲人：聂兰顺

## TCP连接管理

## TCP连接管理

+ TCP sender和receiver在传输数据前需要建立连接

+ 初始化TCP变量
+ - Seq. #
+ - Buffer和流量控制信息

+ Client: 连接发起者

```
Socket clientSocket = new Socket("hostname","port number");
```

+ Server: 等待客户连接请求

```
Socket connectionSocket = welcomeSocket.accept();
```

# Three way handshake:

+ Step 1: client host sends TCP SYN segment to server
+ - specifies initial seq #
+ - no data

+ Step 2: server host receives SYN, replies with SYNACK segment
+ - server allocates buffers
+ - specifies server initial seq. #

Step 3: client receives SYNACK, replies with ACK segment, which may contain data

## TCP连接管理：建立

Client host

Server host

Connection request

Connection granted

ACK

Time

Time

```
SYN=1, seq=client_isn
```

```
SYN=1, seq=server_isn, ack=client_isn+1
```

```
SYN=0, seq=client_isn+1, ack=server_isn+1
```

![](img/b7a9324545f24cd4f1f7132598005229_252_0.png)

## TCP连接管理：关闭

# Closing a connection:

client closes socket: clientSocket.close();

# Step 1: client向server发送TCP FIN 控制segment

# Step 2: server 收到FIN, 回复ACK. 关闭连接, 发送 FIN.

# Step 3: client 收到FIN, 回复ACK.

+ 进入“等待”一如果收到FIN，会重新发送ACK

# Step 4: server收到ACK. 连接关闭.

![](img/b7a9324545f24cd4f1f7132598005229_253_0.png)

## TCP连接管理

TCP client lifecycle

TCP server lifecycle

![](img/b7a9324545f24cd4f1f7132598005229_254_0.png)

![](img/b7a9324545f24cd4f1f7132598005229_254_1.png)

## 哈尔滨工业大学

HARBIN INSTITUTE OF TECHNOLOGY

立足航天，服务国防，面向国民经济主战场

## 谢谢！

## 计算机网络之探幽索隐

主讲人：聂兰顺

## 本讲主题

## 拥塞控制原理(1)

## 拥塞控制

# 拥塞(Congestion)

非正式定义： “太多发送主机发送了太多数据或者发送速度太快，以至于网络无法处理”

表现：

+ - 分组丢失（路由器缓存溢出）
+ - 分组延迟过大（在路由器缓存中排队）

拥塞控制 vs. 流量控制

A top-10 problem.

![](img/b7a9324545f24cd4f1f7132598005229_258_0.png)

## 拥塞的成因和代价：场景1

+ 两个senders,两个receivers
+ 一个路由器,无限缓存
+ 没有重传

![](img/b7a9324545f24cd4f1f7132598005229_259_0.png)

![](img/b7a9324545f24cd4f1f7132598005229_259_1.png)

![](img/b7a9324545f24cd4f1f7132598005229_259_2.png)

+ 拥塞时分组延迟太大
+ 达到最大 throughput

## 拥塞的成因和代价：场景2

+ 一个路由器, 有限buffers

+ Sender重传分组

![](img/b7a9324545f24cd4f1f7132598005229_260_0.png)

## 拥塞的成因和代价：场景2

+ - 情况a: Sender能够通过某种机制获取路由器buffer信息，有空闲才发 λ_in = λ_out (goodput)
+ - 情况b: 丢失后才重发: λ_in' > λ_out
+ - 情况c: 分组丢失和定时器超时后都重发, λ_in' 变得更大

![](img/b7a9324545f24cd4f1f7132598005229_261_0.png)

![](img/b7a9324545f24cd4f1f7132598005229_261_1.png)

![](img/b7a9324545f24cd4f1f7132598005229_261_2.png)

+ - 对给定的"goodput"，要做更多的工作（重传）
+ - 造成资源的浪费

## 拥塞的成因和代价：场景3

+ - 四个发送方
+ - 多跳
+ - 超时/重传

Q: 随着 λ_in 和 λ'_in 不断增加，会怎么样？

![](img/b7a9324545f24cd4f1f7132598005229_262_0.png)
