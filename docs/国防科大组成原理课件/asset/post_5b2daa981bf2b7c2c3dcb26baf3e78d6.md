
## 内存总线——协议层

- 激活、读写、预充电时序

Bank activate command cycle: tRCD = 3, AL = 2, tRP = 3, tRRD = 2, tCCD = 2

tRCD：激活到读写延迟； AL：提前发出读写操作（内部开始的时间是一样的）； tRP：预充电到下次激活的延迟； tRRD：两个激活（针对不同bank）的延迟； tCCD：读写到读写（对不同bank）的延迟； tRC：对同一bank两次激活的延迟；

## 内存总线——内存控制器

- 地址译码
  - 物理地址→SDRAM地址（片选、bank、行、列）
- 命令调度
  - FCFR（First Come First Ready）
  - Bank轮转
- 时序控制
  - 初始化、刷新控制
  - 负责SDRAM的命令发送间隔控制
- 物理接口PHY
  - 单沿双沿转换（并串转换）
  - 信号相位调整（DLL）
  - 数据同步（多个SDRAM）

![](img/0d16039e8c3308af077d6d25bb4413a8_393_0.png)

## IO总线

- 连接处理器与输入输出设备的总线，也称为设备总线
- 局部总线： ISA、 PCI、 AGP、 PCIe、 ……
- 显示总线： VGA、 DVI、 HDMI、 DP、 ……
- 音频总线： AC97、 HDA
- 其他： GMAC、 SATA、 USB

## PCI总线

- PCI = Peripheral Component Interconnect
- 用于扩展外设的局部总线

![](img/0d16039e8c3308af077d6d25bb4413a8_396_0.png)

## PCI总线信号

- 地址&数据
- 控制
- 仲裁
- 时钟复位
- 中断

![](img/0d16039e8c3308af077d6d25bb4413a8_397_0.png)

## PCI总线特性

- 支持多种类型的访问
  - 内存读/写
  - IO读/写
  - 配置读/写
- 三态总线
  - 使用中央仲裁器
  - 支持总线停靠
- 支持软件自动配置
- 支持64位

| C/BE[3:0]# | Command Type |
|---|---|
| 0000 | Interrupt Acknowledge |
| 0001 | Special Cycle |
| 0010 | I/O Read |
| 0011 | I/O Write |
| 0100 | Reserved |
| 0101 | Reserved |
| 0110 | Memory Read |
| 0111 | Memory Write |
| 1000 | Reserved |
| 1001 | Reserved |
| 1010 | Configuration Read |
| 1011 | Configuration Write |
| 1100 | Memory Read Multiple |
| 1101 | Dual Address Cycle |
| 1110 | Memory Read Line |
| 1111 | Memory Write and Invalidate |

## PCI总线事务——写

- AD上无TA周期

![](img/0d16039e8c3308af077d6d25bb4413a8_400_0.png)

## PCI总线仲裁

- 拿到GNT的设备在总线空闲后控制总线
- 总线仲裁可在传输过程中进行

![](img/0d16039e8c3308af077d6d25bb4413a8_401_0.png)

## PCI配置头

- 设备信息
  - 厂商号、设备号
- 状态与控制
  - IO/MEM/DMA/中断使能
  - 中断/能力/错误状态
- 基址
  - 设备向系统声明所需要的空间
  - 系统给设备分配基址
  - [0]: MEM/IO, [3]:可预取
  - 比所占空间高的位可写
- 扩展能力

| 31:24 | 23:16 | 15:8 | 7:0 | 偏移 |
|---|---|---|---|---|
| Device ID | | Vendor ID | | 0x00 |
| Status | | Command | | 0x04 |
| Class Code | Class Code | Class Code | Rev ID | 0x08 |
| BIST | Header Type | Latency Timer | Cache Line Size | 0x0C |
| Base Address Register | | | | 0x10 |
| Base Address Register | | | | 0x14 |
| Base Address Register | | | | 0x18 |
| Base Address Register | | | | 0x1C |
| Base Address Register | | | | 0x20 |
| Base Address Register | | | | 0x24 |
| Card CIS Pointer | | | | 0x28 |
| Subsystem ID | | Subsystem Vendor ID | | 0x2C |
| Expansion ROM Base Address | | | | 0x30 |
| Reserved | Reserved | Reserved | Capabilities Pointer | 0x34 |
| Reserved | | | | 0x38 |
| Max_Lat | Min_Lat | Interrupt Pin | Interrupt Line | 0x3C |

## PCI配置过程

- 找到设备并访问其配置空间
  - 配置访问在PCI初始化前可用，使用片选机制
  - 主板上AD的高位与PCI槽的IDSEL相连
  - 扫描AD高位，发配置访问，如果有响应则发现设备

Type 0：

| 31:11 | 10:8 | 7:2 | 1:0 |
|---|---|---|---|
| Reserved | Function Number | Register Number | 0 0 |

Type 1：

| 31:24 | 23:16 | 15:11 | 10:8 | 7:2 | 1:0 |
|---|---|---|---|---|---|
| Reserved | Bus Number | Device Number | Function Number | Register Number | 0 1 |

- 分配地址空间
  - 读BAR，确定类型
  - 写全1，读，确定申请的空间大小
  - 分配地址，写BAR
- 加载设备驱动
  - 根据设备信息找到对应的驱动，进行设备相关初始化

*PCIe/HT 尽管底层机制完全不同，但软件使用方法一致*

## 计算机体系结构基础

胡伟武、苏孟豪

## 第09章：计算机系统启动过程分析

- 处理器核初始化
- 总线接口初始化
- 设备探测及驱动加载
- 多核启动过程

## 一句话要点

- 系统启动
  - 从复位到系统可用
- 初始化是什么
  - 将系统各种寄存器状态从不确定设置为确定，将一些模块状态从无序强制为有序的一个过程
- 什么东西需要初始化
  - CPU、内存、各类IO接口
- 怎么初始化
  - 按照从核内到核外，从片内到片外的次序进行

## 系统启动过程示意图

![](img/0d16039e8c3308af077d6d25bb4413a8_408_0.png)

## 首条指令

- 初始化CP0（0号协处理器，用于控制处理器行为）
  - 状态寄存器Status
  - 原因寄存器Cause
- 初始化软件约定使用的通用寄存器
  - 栈指针：BIOS用的堆栈
  - 全局指针：BIOS用的地址空间
  - 内核约定物理地址240MB-256MB之间的空间给BIOS用

```
mtc0    zero, COP_0_STATUS_REG        mtc0    zero,c0_sr
mtc0    zero, COP_0_CAUSE_REG         mtc0    zero,c0_cause
li      t0, SR_BOOT_EXC_VEC           lui     t0,0x40
mtc0    t0, COP_0_STATUS_REG          mtc0    t0,c0_sr
la      sp, stack                    lui     sp,0x8f90
la      gp, _gp                      addiu   sp,sp,-16384
                                      lui     gp,0x8f9a
                                      addiu   gp,gp,-8192
```
