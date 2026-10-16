

## 两个中断请求线

- 不可屏蔽，保留用于关键事件。
- 可屏蔽，关闭以忽略或延迟某些中断。
- Intel Pentium 处理器事件向量表：

| vector number | description |
|---|---|
| 0 | 除法错误 |
| 1 | 调试异常 |
| 2 | 空中断 |
| 3 | 断点 |
| 4 | INTO 检测溢出 |
| 5 | 边界范围异常 |
| 6 | 无效操作码 |
| 7 | 设备不可用 |
| 8 | 双重故障 |
| 9 | 协处理器段溢出（保留） |
| 10 | 无效任务状态段 |
| 11 | 段不存在 |
| 12 | 栈故障 |
| 13 | 保护错误 |
| 14 | 页故障 |
| 15 | （Intel 保留，请勿使用） |
| 16 | 浮点错误 |
| 17 | 对齐检查 |
| 18 | 机器检查 |
| 19-31 | （Intel 保留，请勿使用） |
| 32-255 | 可屏蔽中断 |

## 直接内存访问

- 用于避免对大量数据移动使用程序化 I/O
- 需要 DMA 控制器，一种专用处理器
- 绕过 CPU 直接在 I/O 设备和内存之间传输数据
  - 主机将 DMA 命令块写入内存
  - CPU 将该命令块的地址写入 DMA 控制器
  - DMA 控制器直接操作内存总线，将地址置于总线上以执行传输
- DVMA 可以在 CPU 不介入或不使用主内存的情况下在两个内存映射设备之间执行传输。

## 执行 DMA 传输的六步流程

1. 设备驱动程序被告知将磁盘数据传输到地址 X 的缓冲区
2. 设备驱动程序告诉磁盘控制器从磁盘传输 C 字节到地址 X 的缓冲区
3. 磁盘控制器启动 DMA 传输
4. 磁盘控制器将每个字节发送到 DMA 控制器
5. DMA 控制器将字节传输到缓冲区 X，增加内存地址并减少 C，直到 C=0
6. 当 C=0 时，DMA 中断 CPU 以发出传输完成信号

![](img/9321d6c42b8369e67ceb1f1d7e27b09c_842_0.png)

## 直接内存访问（续）

- 从 CPU 接管系统，通过系统总线将数据传输到和来自内存
- 使用周期挪用（周期挪用）通过系统总线传输数据
- 指令周期被挂起以便传输数据
- CPU 暂停一个总线周期
- 不发生中断
  - 不保存上下文

![](img/9321d6c42b8369e67ceb1f1d7e27b09c_843_0.png)

## 13.3 应用 I/O 接口

- I/O 系统调用将设备行为封装在通用类中
- 设备在许多维度上有所不同
  - 字符流或块
  - 顺序或随机访问
  - 同步或异步
  - 可共享或专用
  - 操作速度
  - 读-写、只读或只写
- 设备驱动层隐藏 I/O 控制器之间的差异，使内核免受影响

## 一个内核 I/O 结构

software

kernel

Kernel I/O subsystem

SCSI device driver

keyboard device driver

mouse device driver

...

PCI bus device driver

floppy device driver

ATAPI device driver

hardware

SCSI device controller

keyboard device controller

mouse device controller

...

PCI bus device controller

floppy device controller

ATAPI device controller

SCSI device

keyboard

mouse

...

PCI bus

floppy disk drives

ATAPI devices (disks, tapes, drives)

## I/O 设备的特性

| aspect | variation | example |
|---|---|---|
| 数据传输模式 | character<br>block | terminal<br>disk |
| 访问方法 | sequential<br>random | modem<br>CD-ROM |
| 传输调度 | synchronous<br>asynchronous | tape<br>keyboard |
| 共享 | dedicated<br>sharable | tape<br>keyboard |
| 设备速度 | latency<br>seek time<br>transfer rate<br>delay between operations |  |
| I/O 方向 | read only<br>write only<br>read-write | CD-ROM<br>graphics controller<br>disk |

## 块设备和字符设备

- **块设备包括磁盘驱动器**
  - 命令包括读、写、寻道
  - 原始 I/O 或文件系统访问
  - 可能进行内存映射文件访问
- **字符设备包括键盘、鼠标、串行端口**
  - 命令包括 `get`、`put`
  - 其上分层的库允许行编辑

