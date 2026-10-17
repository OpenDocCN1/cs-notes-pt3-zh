
## Main-Memory Management

- The operating system is responsible for the following activities in connection with memory management: 在同存储管理有关的活动中，操作系统负责下列事务：
    - Keep track of which parts of memory are currently being used and by whom. 保持记录存储器的哪一部分当前被使用以及被谁使用
    - Decide which processes to load when memory space becomes available. 当有可用存储空间时，决定调入哪个进程
    - Allocate and deallocate memory space as needed. 需要时分配和收回存储空间

Discuss in Chap 9-10

## 3.1.3 File Management 文件管理

- A file is a collection of related information defined by its creator. Commonly, files represent programs (both source and object forms) and data. 文件是由其创建者定义的关联信息的一个收集器（集合），通常文件表示程序（源程序和目标程序）和数据

- The operating system is responsible for the following activities in connection with file management: 在同文件管理有关的活动中，操作系统负责下列事务：
    - File creation and deletion. 文件创建和删除
    - Directory creation and deletion. 目录创建和删除
    - Support of primitives for manipulating files and directories. 支持操纵文件和目录的原语
    - Mapping files onto secondary storage. 把文件映象到二级存储器
    - File backup on stable (nonvolatile) storage media. 在稳定（非易失性）存储介质做文件备份

Discuss in Chap 11-12

## 3.1.4 I/O System Management I/O系统管理

- The I/O system consists of: I/O系统包括
    - A buffer-caching system 缓冲区-高速缓存系统
    - A general device-driver interface 通用设备驱动器接口
    - Drivers for specific hardware devices 用于特定硬件设备的驱动程序

Discuss in Chap 13

## 3.1.5 Secondary-Storage Management 二级存储管理

- Since main memory (*primary storage*) is *volatile* and too small to accommodate all data and programs permanently, the computer system must provide *secondary storage* to back up main memory. 由于主存（基本存储器）是易失性的，而且太小不足以永久保存所有的数据和程序，计算机系统必须提供二级存储器备份主存

- Most modern computer systems use disks as the principle on-line storage medium, for both programs and data. 多数现代计算机系统采用磁盘作为程序和数据的基本联机存储介质

- The operating system is responsible for the following activities in connection with disk management: 在同磁盘管理有关的活动中，操作系统负责下列事务：
    - Free space management 空闲空间管理
    - Storage allocation 存储分配
    - Disk scheduling 磁盘调度

Discuss in Chap 14

## 3.1.6 Networking (Distributed Systems) 网络处理（分布式系统）

- **A distributed system** is a collection of processors that do not share memory or a clock. Each processor has its own local memory. 分布式系统是一组不共享存储器或时钟的处理器集合，每个处理器有自己的内存

- **The processors in the system are connected through a communication network.** 系统中的处理器通过通信网络连接

- **Communication takes place using a _protocol_.** 使用协议进行通信

- A distributed system provides user access to various system resources. 分布式系统提供用户访问各种系统资源

- Access to a shared resource allows: 对共享资源的访问可以实现：
    - Computation speed-up 加速运算
    - Increased data availability 提高数据利用性
    - Enhanced reliability 增强可靠性

Discuss in Chap 15-17

## 3.1.7 Protection System 保护系统

- **Protection** refers to a mechanism for controlling access by programs, processes, or users to both system and user resources. 保护是一种机制，控制程序、进程、或用户对系统和用户资源的访问

- The protection mechanism must: 保护机制必须
    - distinguish between authorized and unauthorized usage. 区分授权和非授权使用
    - specify the controls to be imposed. 确定要采用的控制
    - provide a means of enforcement. 提供强制手段

Discuss in Chap 18-19

## 3.1.8 Command-Interpreter System 命令解释系统

- Many commands are given to the operating system by control statements which deal with: 操作系统有许多命令，可以通过控制语句处理：
    - **process creation and management** 进程创建和管理
    - **I/O handling** 处理I/O
    - **secondary-storage management** 二级存储管理
    - **main-memory management** 主存管理
    - **file-system access** 文件访问
    - **protection** 保护
    - **networking** 网络

- The program that reads and interprets control statements is called variously: 读入和解释控制语句的程序有各种名称
    - command-line interpreter 命令行解释器
    - shell (in UNIX)

- Its function is to get and execute the next command statement. 其功能是获得和执行下一个命令语句

![](img/ba81f478b8c7b785e80053d010189a68_80_0.png)

![](img/ba81f478b8c7b785e80053d010189a68_80_1.png)
