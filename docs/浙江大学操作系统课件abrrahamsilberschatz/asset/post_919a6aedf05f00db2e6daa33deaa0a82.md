

## 2.3 Storage Structure 存储构造

### 2.3.1 Main Memory

- Main memory (random-access memory or RAM) – only large storage media that the CPU can access directly.
  主存--CPU可以直接访问的唯一大型存储介质

- Secondary storage– extension of main memory that provides large nonvolatile storage capacity.
  二级(辅助、外)存储器-主存的扩展提供了非易失的存储容量

### 2.3.2 Magnetic disks

- Magnetic disks– rigid metal or glass platters covered with magnetic recording material
  磁盘-覆盖了磁记录材料的硬金属或玻璃盘片

## Storage Structure (Cont.)

- Disk surface is logically divided into *tracks*, which are subdivided into *sectors*.
  磁盘表面逻辑划分了磁道、再划分为扇区

- The *disk controller* determines the logical interaction between the device and the computer.
  磁盘驱动器确定设备和计算机之间的相互作用

- **Positioning time** 定位时间（random-access time 随机存取时间）: consists of the time to move the disk arm to the desired cylinder (called the seek time 寻道时间), and the time for the desired sector to rotate to the disk head (called the rotational latency 旋转延迟时间).

## Fig 2.5 Moving-Head Disk Mechanism 磁头移动机制

![](img/ba81f478b8c7b785e80053d010189a68_45_0.png)

## 2.4.1 Caching缓存

- Use of high-speed memory to hold recently-accessed data.
  用高速存储器保存最近访问的数据

- Requires a _cache management_ policy, can result in 80% to 99% Of all accesses being in the cache.
  需要缓存管理策略

- Caching introduces another level in storage hierarchy. This requires data that is simultaneously stored in more than one level to be _consistent_.
  在存储层次中缓存引入另一级，则要求在更多层次上一致协调被存储的数据

## 2.4.2 Coherency and Consistency
相关性和一致性

- In a hierarchical structure, the same data may appear in different levels of the storage system.
- In a multiprocessor environment, cache coherency is a hardware problem.
- In a distributed environment, several copies of the same file can be kept on different computers.

## Fig 2.7 Migration of A From Disk to Register
从磁盘到寄存器变迁

![](img/ba81f478b8c7b785e80053d010189a68_50_0.png)

## 2.5 Hardware Protection 硬件保护

- 2.5.1 Dual-Mode Operation--两状态运行
- 2.5.2 I/O Protection-- I/O保护
- 2.5.3 Memory Protection--内存保护
- 2.5.4 CPU Protection-- CPU 保护

## 2.5.1 Dual-Mode Operation
两状态运行

- Sharing system resources requires operating system to ensure that an incorrect program cannot cause other programs to execute incorrectly.
  共享系统资源要求操作系统确保一个出错程序不会引起其他程序的运行错误

- Provide hardware support to differentiate between at least two modes of operations.
  至少在两个不同运行状态之间提供硬件支持

1. *User mode—Privileged instructions can not be issued, execution done on behalf of a user.*
   用户态--不能执行特权指令，为用户做的执行

## Dual-Mode Operation (Cont.-1)

2. Monitor mode (also kernel mode or system mode or supervisor) – All instructions can be issued, execution done on behalf of operating system.
   管态（核心态或系统态）-所有指令能使用，为操作系统做的执行

- Mode bit added to computer hardware to indicate the current mode: monitor (0) or user (1). 计算机硬件中增加状态位，指示正确的状态：管态（0）或用户态（1）

- When an interrupt or fault occurs hardware switches to monitor mode. 当中断或错误出现，硬件切换至管态

## Dual-Mode Operation (Cont.-2)

Interrupt/fault
中断 / 错误

set user mode
置用户态

Monitor
管态

User
用户态

Privileged instructions can be issued only in monitor mode.
特权指令只能在管态下使用

![](img/ba81f478b8c7b785e80053d010189a68_54_0.png)

![](img/ba81f478b8c7b785e80053d010189a68_54_1.png)

## 2.5.2 I/O Protection I/O保护

- All I/O instructions are privileged instructions. 所有I/O指令是特权指令

- Must ensure that a user program could never gain control of the computer in monitor mode 在管态模式下必须确保用户程序决不能控制计算机

- Given the I/O instructions are privileged, how does the user program perform I/O? I/O指令是要特权的，用户程序如何完成I/O？

## I/O Protection (Cont.)

- System call – the method used by a process to request action by the operating system.
  系统调用- 方法是进程请求操作系统的一个动作 （功能）
  Usually takes the form of a trap to a specific location in the interrupt vector.
  通常以陷阱形式出现 ， 以指定中断向量的地址
  Control passes through the interrupt vector to a service routine in the OS, and the mode bit is set to monitor mode. 控制通过中断向量传递给OS中的服务程序， 状态位设为管态
  The monitor verifies that the parameters are correct and legal, executes the request, and returns control to the instruction following the system call.
  监控程序验证参数正确合法，执行请求， 返回控制给系统调用后的指令

