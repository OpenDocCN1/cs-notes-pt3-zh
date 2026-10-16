
## 数据链路层(Data-Link)

![](img/4ebfc3970286fe7ea98cf4db2323e179_40_0.png)

## 网络层 (Network)

- 任务：交换、路由、拥塞控制、网际互连
- 网络层处理任意节点的数据传输
- 传输的信息单位是分组 (Packet)

![](img/4ebfc3970286fe7ea98cf4db2323e179_42_0.png)

## 传输层(Transport)

- 端到端的通信, 把数据可靠的从一端用户进程送到另一端用户进程。
- 端到端的流量控制
- 端到端的差错控制

传输的信息单元是报文(Message)

![](img/4ebfc3970286fe7ea98cf4db2323e179_44_0.png)

## 会话层(Session)

两个计算机上的用户进程建立连接，双方互相确认身份，协商会话连接的细节。

![](img/4ebfc3970286fe7ea98cf4db2323e179_45_0.png)

## 表示层(Presentation)

解决用户信息的语法问题,对用户数据进行翻译、编码和变换

![](img/4ebfc3970286fe7ea98cf4db2323e179_46_0.png)

## 应用层(Application)

处理用户的数据和信息，完成用户所希望的实际任务。

![](img/4ebfc3970286fe7ea98cf4db2323e179_47_0.png)

## OSI参考模型各层功能总结

Application
To allow access to network resources

Presentation
To translate, encrypt, and compress data

Session
To establish, manage, and terminate sessions

Transport
To provide reliable process-to-process message delivery and error recovery

Network
To move packets from source to destination; to provide internetworking

Data link
To organize bits into frames; to provide hop-to-hop delivery

Physical
To transmit bits over a medium; to provide mechanical and electrical specifications

## 1.4.4 TCP/IP网络体系结构

- TCP/IP: (Transmission Control Protocol/ Internet Protocol) 是世界上最大的计算机网络Internet 运行的基础，是目前应用最广泛的网络通信协议。
- **OSI/RM**的制定具有十分重大的意义，但是由于TCP/IP协议得到普遍使用，所以在计算机网络领域一般认为TCP/IP是事实上的工业标准，在实际运行的系统中采用OSI模型的并不多。尽管如此，**OSI**模型仍然对建立计算机网络具有重要的指导意义。

## OSI模型

## TCP/IP

应用层

表示层

会话层

传输层

网络层

数据链路层

物理层

应用层

SMTP

FTP

TELNET

DNS

SNMP

GOPHER

HTTP

NNTP

传输层

TCP

UDP

网络层

ICMP

IP

IGMP

ARP

RARP

数据链路层

该层协议由底层网络定义

物理层

该层协议由底层网络定义

## RFC文档

- 所有关于Internet网络的正式标准都以RFC（Request for Comment）文档出版。出版的目的只是为了提供相关的信息。RFC文档的每一项都用一个数字来标识，例如RFC983，数字值越大说明RFC文档的内容越新。
- 所有的RFC文档都可以网络上免费获得。
- http://www.cnpaf.net/
- 中国协议分析网

## 1.5 实体间通信与服务

在计算机网络中，每层的功能由该层的实体来实现，下层实体为上层实体提供服务。上层通过下层的服务完成自己的功能。

## 1.5.1 层间通信与对等层间通信

- 层间通信:同一节点上相邻层次的通信。
- 对等层间通信：不同的网络节点上对等层间的通信。
- 实通信：层间通信和物理层之间的通信
- 虚通信：除物理层之外，对等层间的通信。

## 发送进程

## 接收进程

应用层

表示层

对话层

传输层

网络层

数据链路层

物理层

发送主机

应用层

表示层

对话层

传输层

网络层

数据链路层

物理层

接收主机

Data

AH Data

PH AH Data

SH PH AH Data

TH SH PH AH Data

NH TH SH PH AH Data

DH NH TH SH PH AH Data DT

比特序列

## 1.5.2 服务与数据单元

数据在网络中各节点内是沿层次传送的。每层为其上面各层提供专门的通信服务。也就是说,每层完成的功能是其上各层工作的基础。

N层向N+1层提供服务。N层是服务提供者,N+1层是用户,服务是通过一组服务原语来执行的。

## 1.5.2 服务与数据单元

- 层间接口处提供服务的地方称为服务访问点SAP (Service Access Point)
- 相邻层在提供服务的过程中要传递信息，这些信息称为服务数据单元SDU（Service Data Unit）。
- 对等层间交换的信息单位称为协议数据单元PDU（Protocol Data Unit）

## 1.5.2 服务与数据单元

- N层的PDU由N层的SDU加上该层的协议控制信息PCI（Protocol Control Information）构成。
- (N+1) PDU --> (N) SDU
- (N) SDU+ (N) PCI --> (N) PDU

![](img/4ebfc3970286fe7ea98cf4db2323e179_58_0.png)

## 各种数据单元的关系

![](img/4ebfc3970286fe7ea98cf4db2323e179_59_0.png)

## PDU 与SDU的关系

(N+1)PDU是通过(N)SDU传递到N层，加上(N)PCI后构成(N)PDU的。看上去似乎(N+1)PDU就等同于(N)SDU，虽然在许多情况下确实如此，但却并不总是这样。有时可以将多个(N+1)PDU拼成一个(N)SDU，称为拼接（Concatenation）。当然，在发送方若进行了拼接，在接受方的对等层就要进行相反的分割（Separation）。另外，一个(N)SDU若太大，也可以分成若干段，分别加上协议控制信息，构成多个(N)PDU。这在发送方称为分段（Segmenting），而接收方则要进行相反的合段（reassembling）。

n+1 层

n 层

n-1 层

复用

Muitiplexing

分用

Segaration

分裂

Spiliting

聚合

Recombine

复用/分用

分裂/聚合

![](img/4ebfc3970286fe7ea98cf4db2323e179_61_0.png)
![](img/4ebfc3970286fe7ea98cf4db2323e179_61_1.png)
![](img/4ebfc3970286fe7ea98cf4db2323e179_61_2.png)
![](img/4ebfc3970286fe7ea98cf4db2323e179_61_3.png)

## 主机1向主机2发送数据

应用进程数据先传送到应用层
加上应用层首部，成为应用层 PDU

![](img/4ebfc3970286fe7ea98cf4db2323e179_62_0.png)

## 主机 1 向主机 2 发送数据

主机 1

AP₁

应用层 PDU 再传送到运输层
加上运输层首部，成为运输层报文

主机 2

AP₂

## 主机 1 向主机 2 发送数据

主机 1

AP₁

5

4

3

2

1

运输层报文再传送到网络层

加上网络层首部，成为 IP 数据报（或分组）

主机 2

AP₂

5

4

3

2

1

## 主机 1 向主机 2 发送数据

![](img/4ebfc3970286fe7ea98cf4db2323e179_65_0.png)

IP 数据报再传送到数据链路层
加上链路层首部和尾部，成为数据链路层帧
