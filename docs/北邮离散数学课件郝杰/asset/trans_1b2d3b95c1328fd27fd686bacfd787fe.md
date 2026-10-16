

## ISO的信息安全体系结构

- ISO 7498-2 规定的“开放系统互连安全体系结构”，（GB-T 9387.2-1995 信息处理系统开放系统互连基本参考模型第2部分：安全体系结构）

- 给出了基于 OSI 参考模型的七层协议之上的信息安全体系结构，它定义了开放系统的五大类安全服务，以及提供这些服务的八大类安全机制及相应的 OSI 安全管理，并可以根据具体系统适当地配置于 OSI 模型的七层协议中。

## 信息安全体系结构

![](img/ec5c59e5ed61c3b45834fc86d9ef22ae_123_0.png)

## § 1.7 计算机网络和因特网的历史及进展

### 60年代：面向终端分布的计算机系统

![](img/ec5c59e5ed61c3b45834fc86d9ef22ae_124_0.png)

### 计算机网络和因特网的历史

- 60年代中期，当时正处于冷战的最紧张时期，前苏联的任何攻击都会连带损坏美国的整个电话系统，倘若如此，美国将丧失军事通信能力。
- 电话系统是高度集中式的，即使主要系统的一小部分遭到损坏，所有的长途通信也都会被中断。

### 70年代：分组交换数据网(PSDN)出现

以美国国防部高级研究计划局DARPA的 ARPANET为代表，采用崭新的“存储转发--分组交换”原理，它标志着计算机网络的兴起。

![](img/ec5c59e5ed61c3b45834fc86d9ef22ae_126_0.png)

IMP：接口报文处理机

### 80年代：LAN和互连网发展、综合业务数字网

ISDN和智能网IN的出现

80年代中，以ISO/OSI七层模型为参照，ISO和国际电报电话咨询委员会CCITT为各个层次制定了一系列协议标准，组成了一个庞大的基本标准集，同时也为OSI的应用和产品的最终实现制定功能标准或轮廓标准ISP（International Standardized profile）。

### 90年代：现代网络技术

- 高速以太网（百兆、千兆网），
- 三层交换技术、
- ATM技术
- VLAN……

## 历年连接到因特网的国家数

![](img/ec5c59e5ed61c3b45834fc86d9ef22ae_129_0.png)

## 谁管理因特网？

http://xplanations.com/whorunstheinternet/

### HERE IS HOW IT WORKS.

![](img/ec5c59e5ed61c3b45834fc86d9ef22ae_131_0.png)

### THE INTERNET

POLICIES & STANDARDS GUIDE THE WAY IN DECISION MAKING

### MULTI-STAKEHOLDERS

Civil Society & Internet Users, the Private Sector, Governments, National & International Organizations, Research, Academic and Technical Communities all have a say in how the Internet is run.

### OPEN DEBATE

The formal and informal process of debating policy and standard proposals in multi-stakeholder model using any variety of methods; in-person, Internet Drafts, public forums, publishing, and many more.

### POLICIES & STANDARDS

Internet policies are the shared principles, norms, rules, decision-making procedures, and programmes that shape the evolution and use of the Internet. Internet Standards enable interoperability of systems on the Internet by defining protocols, messages formats, schemes and languages.

### OPERATIONS & SERVICES

Internet Operations span all aspects of hardware, software, and infrastructure required to make the Internet work. Services include education, access, web browsing, online commerce, social networking, etc.

Operations & Services support the Internet's global infrastructure.

## 因特网的标准：RFC

- 因特网工程任务组（IETF，Internet Engineering Task Force）
  - 面向近期标准的组织，它分为9个领域（应用、寻径和寻址、安全等等），负责开发成为因特网标准的规范。
- RFC: Request For Comments
  - 因特网的标准文档

## 本章内容总结

- 1.1 计算机网络和因特网的概念及其应用：
  计算机网络、互联网、Internet(因特网)、WWW (万维网)、计算机网络的组成
- 1.2 网络边缘： 局域网、网络接入方式
- 1.3 网络核心： 广域网、电路交换和分组交换、 ISP和骨干网
- 1.4 衡量网络性能的指标： 带宽、时延、吞吐量
- 1.5 协议和层次体系结构： 协议、分层的体系结构、OSI参考模型、TCP/IP协议栈
- 1.6 计算机网络的安全隐患
- 1.7 计算机网络和因特网的历史及进展

## 版权说明

本讲义中部分图片来源于下列教材所附讲义：

- Jim Kurose, Keith Ross, Computer Networking: A Top Down Approach, 7th Edition, Pearson/Addison Wesley, April 2016, 引用时标记为[Kurose];
- Andrew S. Tanenbaum, Computer Networks, Fourth Edition, 清华大学出版社（影印版）, 2004, 引用时标记为[Tanenbaum];
- 谢希仁，计算机网络，第五版，电子工业出版社，2008年1月,引用时标记为[谢];
- Behrouz A. Forouzan, Data Communications and Networking, Fourth Edition, McGraw-Hill Higher Education, 2007年1月, 引用时标记为[Forouzan]

## 本章实验：Windows 网卡配置实验

### 实践思考题

- 1）自动获取IP地址是如何实现的？除了IP地址之外，还可以配置哪些参数？
- 2）ping 命令有哪些选项？命令输出的结果中，各个参数有什么含义？

### 拓展思考题

- 选择一个新兴网络应用，查阅资料，了解该应用的功能和性能指标、需要的技术支持等。

## 本章勘误表

| 页码 | 位置 | 原文 | 更正 |
| --- | --- | --- | --- |
| 5 | 第4段第3行 | 桥接器 | 网桥 |
| 6 | 图1-3名 | 端系统之间的通信方式 | 端系统之间的P2P通信方式 |
| 8 | 倒数第2段第1行 | 数百英尺范围内 | 100米内 |
| 20 | 倒数第4行 | 提示型原理 | 指示型原语 |
| 27 | 图1-19下第4行 | 默认网关：192.168.199.1 | 默认网关：192.168.199.127 |

## 主要内容

- 2.1 网络应用概述
- 2.2 DNS
- 2.3 WWW应用和HTTP
- 2.4 Email应用
- 2.5 FTP
- 2.6 远程登录协议：Telnet
- 2.7 应用层安全隐患


