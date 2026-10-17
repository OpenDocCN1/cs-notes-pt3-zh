
## 1.6 Clustered Systems 集群系统

- Clustering allows two or more systems to share storage and are closely linked via LAN network. 集群允许两个或多个系统共享存储器和通过局域网连接。
- Provides high availability (reliability). 提供高可靠性
- A layer of Cluster software runs on the cluster nodes. Each node can monitor one or more of the others (over the LAN).
- Asymmetric clustering: one host is in hot standby mode while the other is running the application. The hot standby host does nothing but monitor the active server. 非对称集群：当另一个服务器正在运行应用程序时，一个主机处在激活等待状态。该机不做任何工作，但监控运行的服务器。
- **Symmetric clustering**: all N hosts are running the application, and they are monitoring each other. 对称集群：当所有的主机都运行应用程序时，他们相互监控。
- **Parallel clusters 并行集群**: allow multiple hosts to access the same data on the shared storage. Parallel clusters are usually accomplished by special versions of software and special releases of applications, for example, Oracle Parallel Server.
- **Clustering over a WAN**:

## 1.7 Real-Time Systems 实时系统

- Rigid time requirements have been placed on the operation of a processor or the flow of data. 严格的时间要求
- Often used as a control device in a dedicated application such as controlling scientific experiments, medical imaging systems, industrial control systems, and some display systems. 通常作为控制设备在诸如控制科学实验、医学影像系统、工业控制系统以及一些显示系统中应用
- Well-defined fixed-time constraints. 严格确定的时间限制
- Real-Time systems may be either *hard* or *soft* real-time. 实时系统可以是硬实时或软实时
- Hard real-time 硬实时：Guarantee that critical task be completed on time.

### Real-Time Systems (Cont.)

Secondary storage is limited or absent, data is stored in short-term memory or read-only memory (ROM). 有限的或没有次级存储器，数据存在短期存储器或只读存储器中。Conflicts with time-sharing systems, not supported by general-purpose operating systems. 同分时系统冲突，通用操作系统不支持

- Soft real-time 软实时：A critical task gets priority over other tasks, and retains that priority until it completes.
- Limited utility in industrial control or robotics. 在工业控制或机器人中有部分应用
- Useful in applications (multimedia, virtual reality) requiring advanced operating-system features. 在需要高级操作系统功能的应用软件（多媒体、虚拟现实）中使用

## 1.8 Handheld Systems 手持系统

- Include: Personal Digital Assistants (PDAs) 个人数字助理，例如 PalmPilots or cellular telephones with connectivity to a network such as the Internet.
- Property: the limited size of such devices
- Issues: 问题
  - Limited memory 内存限制 – manage memory efficiently, do not use virtual memory techniques
  - Slow processors 处理器速度慢 – to be designed not to tax the processor
  - Small display screens 显示屏小 – web clipping for displaying the content in web pages

### Fig 1.6 Migration of Operating-System Concepts and Features
操作系统概念和特性的变迁

![](img/ba81f478b8c7b785e80053d010189a68_29_0.png)

1950　1960　1970　1980　1990　2000

| System type | Features |
| --- | --- |
| mainframes | no software<br>compilers<br>batch<br>resident monitors<br>time shared<br>MULTICS<br>multiuser<br>networked<br>UNIX<br>distributed systems<br>multiprocessor<br>fault tolerant |
| minicomputers | no software<br>compilers<br>resident monitors<br>time shared<br>multiuser<br>networked<br>clustered<br>UNIX<br>multiprocessor<br>fault tolerant |
| desktop computers | no software<br>compilers<br>interactive<br>multiuser<br>networked<br>UNIX<br>multiprocessor |
| handheld computers | UNIX<br>compilers<br>no software<br>interactive<br>networked |

## 1.10 Computing Environments 计算环境

- 1.10.1 Traditional computing（传统的计算）: typical office environment
- 1.10.2 Web-Based Computing（基于Web计算）: Network computers are essentially terminals that understand web-based computing.
- 1.10.3 Embedded Computing（嵌入计算）: to run embedded real-time operating system; to have very specific tasks; provide limited features: little or no user interface, preferring to spend their time monitoring and managing hardware devices.

## Chapter 2: Computer-System Structures 计算机系统结构

- 2.1 Computer System Operation（计算机系统运行）
- 2.2 I/O Structure（I/O结构）
- 2.3 Storage Structure（存储构造）
- 2.4 Storage Hierarchy（存储层次）
- 2.5 Hardware Protection（硬件保护）
- 2.6 Network Structure（网络结构）
