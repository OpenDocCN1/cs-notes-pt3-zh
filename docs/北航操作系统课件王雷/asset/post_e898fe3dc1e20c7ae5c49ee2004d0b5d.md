
## 1965~1980年 集成电路 & 多道程序设计

- 多道程序设计技术
- OS/360开发失败，导致了软件工程的诞生，从另一个意义上说，它也有成功之处，改变了上一代操作系统的问 题，提出了多道程序设计(进程)、向下兼容的思想。商业上成功。
- 分时系统，CTSS、MULTICS、UNIX。

## System/360

- 需求
  - 多数厂商有几条完全不同的生产线，生产不同的计算机，开发和维护完全不同的产品，对于商来说是昂贵的
  - 新用户在开始时只需要一台小计算机，后来可能需要一台大的计算机，而且希望能在新计算机上执行原有的程序。这样，厂家和用户需要软件在不同型号的计算机之间兼容

- 1964 年 IBM 宣布推出 System/360 计算机系统
  - 是第一个采用规模集成电路的主流机型
  - 所有的计算机都有相同的体系结构和指令集
  - 在理论上，为一型号编写的程序可以在其他型号机器上运行

## 陷入泥潭的巨兽

- IBM无法写出同时满足互冲突需要的操作系统，其实别人也一样不能完成这项工作任务
- 数千名程序员写的数百万行汇编语言代码，系统自身占据了大量存储空间和一半的CPU时间
- 数百万行汇编代码中有成千上万处错误，IBM不断发行新的版本试图更正这些错误
- 每个新版本在更正老错误的同时又引入新错误，所以随着时间的流逝，错误的数量大致保持不变
- IBM 的 OS/360 发布时，带着已知的 1000 个错误

![](img/861c0ad57b0249095c0356c9e5a83b26_63_0.png)

## 多道程序系统需要解决的问题

- 在一个连续的内存空间，同时驻留多道程序。
- 处理机的争夺
- I/O设备的分配
- 有效的组织不同程序的运行
- 系统对各种存储介质的管理

## “分时”的含义

分时是指多个用户分享使用同一台计算机。多个程序分时共享硬件和软件资源

- 多个用户分时
- 前台和后台程序（foreground & background）分时
- 时间片（time slice）

## 分时系统的特征

- 多路性：多路连接；宏观上用户共享，微观上分时；
- 独立性：用户相互不干扰；
- 及时性：响应时间；
- 交互性：人机对话。

## 影响响应时间的因素

- 系统开销
- 用户数目
- 时间片
- 对换信息量
- 采用可重入文件
- 引入虚存减少对换

## 1980~1990年 PC机 & 微机操作系统

- PC机
- MSDOS、 WINDOWS 95、 WINDOWS NT、 WINDOWS 2000
- 类UNIX(Linux, Freebsd等)。

|  | 1981 | 2006 | Factor |
|---|---:|---:|---:|
| CPU MHz,<br>Cycles/inst | 10<br>3–10 | 3200×4<br>0.25–0.5 | 1,280<br>6–40 |
| DRAM capacity | 128KB | 4GB | 32,768 |
| Disk capacity | 10MB | 1TB | 100,000 |
| Net bandwidth | 9600 b/s | 1 Gb/s | 110,000 |
| # addr bits | 16 | 32 | 2 |
| #users/machine | 10s | ≤ 1 | ≤ 0.1 |
| Price | $25,000 | $4,000 | 0.2 |

## 1990~ 年 分布式与嵌入式系统

- Cluster of Workstation, Network of Workstation, Grid, Cloud
- 实时操作系统：Psos, VRTX, RTLinux, VxWorks

- The Network is the OS
  - Functionality spread throughout network

Scalable, Reliable, Secure Services

Mobile, Ubiquitous Systems

MEMS for Sensor Nets

## 计算机硬件简介

- 硬件是基础，必须了解硬件。
- 但不必象硬件工程师那样，我们了解的是功能、接口和状态。

![](img/861c0ad57b0249095c0356c9e5a83b26_74_0.png)

## Sparc

## Diagram of Sparc Workstation

![](img/861c0ad57b0249095c0356c9e5a83b26_75_0.png)

## 异常(exceptions)：陷阱(trap)和中断(interrupts)

- 中断是异步异常，可能随时发生，与处理器正在执行的内容无关。中断主要由I/O设备、处理器时钟或定时器产生，可以被启用或禁用。(Asynchronous Exceptions)
- 同步异常，它是某一特定指令执行的结果。在相同条件下，异常可以重现。例如内存访问错误、调试指令以及被零除。(Synchronous exceptions)
- 系统调用也视作同步异常，或trap。
- 软件和硬件都可以产生异常和中断。
- 陷阱(trap)帧：完整的线程描述表的子集，用于现场保护
- 陷阱处理程序处理少量事件，多数转交给其他的内核或执行体模块处理

![](img/861c0ad57b0249095c0356c9e5a83b26_77_0.png)

![](img/861c0ad57b0249095c0356c9e5a83b26_78_0.png)

## 用户进程

线程

read()

用户态

系统调用接口

核心态

陷阱

中断是轻量级的，通过调度中断线程完成大部分的工作

系统调用

中断

中断线程

内核线程

虚拟内存管理器

## System call (1)

![](img/861c0ad57b0249095c0356c9e5a83b26_79_0.png)

## System call(2)

![](img/861c0ad57b0249095c0356c9e5a83b26_80_0.png)

## 硬件中断处理过程

![](img/861c0ad57b0249095c0356c9e5a83b26_81_0.png)

Peripheral Device Controller

CPU Interrupt Controller

CPU Interrupt Service Table

ISR Address
Spinlock
Dispatch
Interrupt Object

Raise IRQL
Grab spinlock

Drop spinlock
Lower IRQL

Read from device

Acknowledge interrupt

Request DPC

KiInterruptDispatch

Driver ISR

## 操作系统的基本类型

- 批处理系统
- 分时系统
- 实时系统
- 混合型

## 实时系统

- 嵌入式OS比桌上PC的OS相对简单，但由于各种嵌入式系统产品中包含各不相同的特殊需求，导致这类系统中使用的OS不下几百种，例如Windows CE、Palm OS、VxWorks、pSOS、QNX、PowerTV、OpenTV、JavaOS、LynxOS、Nucleus等等都是。而且至今仍有一半的开发者使用自行开发的OS。

## 操作系统的特征

- 并发
- 共享
  - 互斥共享（打印机、变量）
  - 同时访问（宏观）
- 虚拟
  - 多道程序中的 CPU
  - SPOOLING（外围设备同时联机操作）
  - 虚拟存储
- 不确定
  - 程序执行结果不确定
  - 多道程序中执行顺序不确定

## 处理机管理

- 进程（线程）控制；
- 进程（线程）同步；
- 进程通信；
- 进程（线程）调度。

## 存储器管理

- 任务：
  - 为多道程序的并发提供良好的环境
  - 便于用户使用存储器
  - 提高存储器利用率
  - 为尽量多的用户提供较大的存储空间
- 功能：
  - 内存分配：静态和动态分配。
  - 内存保护；
  - 地址影射；
  - 内存扩充。

![](img/861c0ad57b0249095c0356c9e5a83b26_87_0.png)
