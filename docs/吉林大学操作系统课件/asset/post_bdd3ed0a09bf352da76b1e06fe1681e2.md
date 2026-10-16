
## 信号(signal)

- 信号处理程序的定义
  - 系统调用 signal(sig,func) 预置,
    - 其中 sig 为 0~19 的信号值， func 为处理程序的地址.
  - 该系统调用的作用是 u_signal[sig]=func.
    - 当 func 为 0 时接收信号进程终止自己;
    - 当 func 为奇数时忽略信号;
    - func 为偶数时为处理程序入口.
  - 进程初创时自动继承其父进程的信号处理程序.

## 信号(signal)

- 信号的发送与接收
  - 进程实际接收到的信号被记载在 p_sig 中。
  - 由于 p_sig 常驻内存，因而在任何时刻均可接收到信号。
  - 信号可能来自进程，也可能是事件，如键盘中断信号、错误、定时器。
  - 处于等待状态的进程在接收到信号后一般将被唤醒。

## 信号(signal)

- 信号的处理
- 接收到信号的进程在适当时刻(被调度选中由核态转到目态)，发现p_sig中记录有接收到的信号，根据u_signal[p_sig]的值确定对信号的处理。
- 接收信号的进程也可以忽略信号 (u_signal[p_sig]==奇数). 对多数信号的缺省处理动作是终止收到信号的进程。
- 信号很像允许用户程序在目态处理的中断。

## 管道(Pipes)

使用方法：先创建管道，再创建进程—继承

```
int fd[2];
```

...

```
pipe(fd)
```

...

```
p1=fork(); p2=fork();
```

p1: write(fd[1],...);      p2:read(fd[0],...)

![](img/7b6892715d0da57dced81602d7459e7e_892_0.png)

## 套接字(socket)

- 端-端通讯机制
  - (endpoint—endpoint)
- 类型
  - *Stream sockets*
  - *Sequenced packet sockets*
  - *Datagram sockets*
  - *Reliably delivered message sockets*
  - *Raw sockets*

## 套接字(socket)

- 地址域
  - 使用中的socket与一地址相联系
    - 地址的形式由通讯域(communication domain)确定.
  - 同一域中的进程使用相同地址格式
    - address format
  - 4.3BSD域
    - UNIX domain (AF_UNIX)
    - the Internet domain (AF_INET)
    - the XEROX Network Service (NS) domain (AF_NS)

## 13.4 存储管理

- 经典UNIX存储管理
  - 一个进程两个对界
    - Text(共享)
    - Data(私有)
  - 内外存不同尺寸，同一管理程序(FF算法)
    - Core: 64bytes
    - swap: 512bytes
  - 交换技术
    - swapping

### 13.4.1 存储管理方式

- 采用界地址存储管理方式
  - 一个进程由两个对界组成, 即占有两个连续的内存区域
    - 一个区域用于保存共享代码
    - 另一个区域用于保存私有数据及用户堆栈
  - 存储分配的基本单位是64个字节, 而不是单个字节

### 13.4.2 存储分配算法

- 内存空间及外存交换区的分配均是动态的, 分配算法为最先适应 (FF).
- 描述内存空间及外存空间分配状况各需有一个数据结构.
- 内存的分配与外存的分配共用同一个程序.

### 13.4.3 进程空间扩充

- 堆栈分配
  - 基本长度，避免浪费
- 堆栈溢出
  - 动态扩展
    - 申请一个新的数据区(原区域大小+增加大小)
    - 复制
    - 释放原有区域
- 内存不够
  - 交换到外存(同时扩展空间)
  - 释放所占内存
  - 再次由sched调入内存时，按新长度

### 13.4.4 交换技术(swapping)

- 交换目标：缓解内存紧张矛盾
- 交换进程：sched(#0)
- 交换算法
  - 移入外存中SRUN状态进程
  - 如内存不够，选择移出
    - 内存中处于SWAIT或SSTOP状态进程
  - 如还不够，选择移出
    - 内存中处于SSLEEP或SRUN状态进程，条件
      - 待移入进程在外时间>=3秒
      - 待移出进程在内时间>=2秒

### 13.4.5 虚拟页式(Paging)

- 4.3BSD UNIX: *demand-paging* + *swapping*
  - 主要依赖(first paging)
  - 其次是交换(secondary swapping).
- 偷页进程(Page stealer process)
  - 动态跟踪并调整进程页架数
  - 基于工作集模型(*working set model*).
- If the *scheduler* decides that the paging system is overloaded, processes will be swapped out *whole* until the overload is relieved.

## 页面置换

### pagedaemon process

- Uses a modified *second-chance* page-replacement algorithm.
- *Second chance*: a variant of NUR.

Set page 3,4 reference bit to 0, replace page 5

![](img/7b6892715d0da57dced81602d7459e7e_901_0.png)

## 页面置换

### pagedaemon process

- Uses a modified *second-chance* page-replacement algorithm.
- *Second chance*: a variant of NUR.

Set page 3,4 reference bit to 0, replace page 5

![](img/7b6892715d0da57dced81602d7459e7e_902_0.png)

## 页面置换

### pagedaemon process

- Uses a modified *second-chance* page-replacement algorithm.
- *Second chance*: a variant of NUR.

Set page 3,4 reference bit to 0, replace page 5

![](img/7b6892715d0da57dced81602d7459e7e_903_0.png)

## 13.5 UNIX文件系统

- 文件类型
- 文件体系
- 文件结构
- 文件目录
- 文件系统映射
- 文件卷安装
- 磁盘空间管理
- Inode区管理
- 快速文件系统
- NFS文件系统

### 13.5.1 文件类型

- 普通文件
  - 内容可以是程序、数据、图象等，保存在磁盘块中
- 目录文件
  - (文件名，文件号)序列，保存在磁盘块中
- 特殊文件
  - 设备
    - 设备作为文件管理的好处
      - 界面统一，使用文件与使用设备命令相同，申请设备open, 释放close, 读read, 写write
      - 利用文件保护功能可以保护设备

### 13.5.2 文件体系

- 基本结构：树型
  - 系统目录，系统文件
  - 用户目录，用户文件
- 连接(link)
  - 不是真正的树，而呈格结构
  - 连接方便文件共享
