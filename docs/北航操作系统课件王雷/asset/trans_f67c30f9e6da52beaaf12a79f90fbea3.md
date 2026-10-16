

## GNU / LINUX

- GNU（GNU 不是 Unix）
- Linux 成为了一个操作系统。值得注意的是 Linux 并没有包括 Unix 源码。它是按照公开的 POSIX 标准重新编写的。Linux 大量使用了由麻省剑桥免费软件基金的 GNU 软件，同时 Linux 自身也是用它们构造而成。

## DOS操作系统

- 微软公司在1981年开发了 MS DOS1.0，4000行汇编语句，运行在 Intel 8086 上。后来 IBM 推出了带硬盘的 PC XT，
- 微软公司在1983年开发了 MS DOS2.0，2.0有了一些类 UNIX 的功能，例如 I/O 重定向。
- 在1984年 IBM 推出了包含80286的 PC AT，微软公司开发了 MS DOS3.0，但是 DOS 3.0 没有发挥出80286的优势。接着微软公司开发了 MS DOS3.1，支持共享文件、网络功能。在1987年推出了 DOS3.3 支持 IBM 推出了新型机 PS/2。

## Windows操作系统

- 在486、Pentium芯片问世后，DOS不能充分发挥硬件性能，因此从80年代初，微软开始开发 GUI。1990年推出了 WINDOWS 3.0，但需基于DOS上运行。1996年推出 Windows 95，后来的 Windows 98。
- IBM在1987年开发的 OS/2 在286保护模式下运行。在与 IBM 分道扬镳后，微软开发了 WINDOWS NT（单用户多任务）。
- 1993年推出了第一个版本的 WINDOWS NT3.1（WINDOWS 3.1风格）。NT4.0（WINDOWS 95）风格。现在的 Windows 2000 是合二为一的操作系统。

## 小结

- 什么是操作系统
- 操作系统的历史
- 操作系统的类型
- 操作系统的特征
- 操作系统的功能
- 操作系统的结构
- 常见的操作系统

## 计算机操作系统

教师：王雷

助教：王振 赵玉龙 王宇 王鲁俊

82316284，wanglei@buaa.edu.cn，http://219.224.165.31

## Linux 如何启动？

![](img/861c0ad57b0249095c0356c9e5a83b26_125_0.png)

## 启动顺序

- 1. 打开电源
- 2. CPU 跳转到 BIOS 的地址（0xFFFF0）
- 3. BIOS 运行 POST（加电自检）
- 4. 查找可启动设备
- 5. 从 MBR 加载并执行引导扇区
- 6. 加载操作系统

## BIOS（基本输入/输出系统）

- BIOS 是指计算机首次通电时运行的软件代码。
- BIOS 的主要功能是嵌入在芯片中的代码程序，用于识别和控制组成计算机的各种设备。

![](img/861c0ad57b0249095c0356c9e5a83b26_128_0.png)

![](img/861c0ad57b0249095c0356c9e5a83b26_128_1.png)

## 引导加载程序

## MBR（主引导记录）

- 操作系统从硬盘启动，主引导记录（MBR）包含主引导加载程序。
- MBR 是一个 512 字节的扇区，位于磁盘的第一个扇区（0 柱面，0 磁头的第 1 扇区）。
- 当 MBR 被加载到 RAM 后，BIOS 将控制权交给它。

![](img/861c0ad57b0249095c0356c9e5a83b26_131_0.png)

- 前 446 字节是主引导加载程序，包含可执行代码和错误信息文本。
- 接下来的 64 字节是分区表，包含四个分区中每个分区的记录。
- MBR 以两个字节结束，定义为魔数（0xAA55）。该魔数用作 MBR 的有效性检查。

## 提取 MBR

- 要查看 MBR 的内容，请使用以下命令：
- `# dd if=/dev/hda of=mbr.bin bs=512 count=1`
- `# od -xa mbr.bin`

dd 命令需要以 root 身份运行，它从 /dev/hda（第一个集成驱动电子设备，即 IDE 驱动器）读取前 512 个字节，并将其写入 mbr.bin 文件。

od 命令以十六进制和 ASCII 格式打印二进制文件。

## 引导加载程序

- 引导加载程序更恰当地说应称为内核加载程序。这一阶段的任务是加载 Linux 内核。
- 可选的初始 RAM 磁盘。
- GRUB 和 LILO 是最流行的 Linux 引导加载程序。

## 其他引导加载程序（多种操作系统）

- bootman
- GRUB
- LILO
- NTLDR
- XOSL
- BootX
- loadlin
- Gujin
- Boot Camp
- Syslinux
- GAG

## LILO：Linux 加载器

- 不依赖于特定的文件系统
- 可以从硬盘和软盘启动
- 最多支持 16 个不同的映像
- 当内核映像文件或配置文件发生变化时，必须更新 LILO

## 内核的任务

- 进程管理
- 内存管理
- 设备管理
- 系统调用

## Linux 内核启动的主要功能流程

| 功能 | 文件 |
|---|---|
| start () | ./arch/i386/boot/head.S |
| startup_32 () | ./arch/i386/boot/compress/head.S |
| decompress_kernel() | ./arch/i386/boot/compress/misc.c |
| startup_32 () | ./arch/i386/kernel/head.S |
| start_kernel () | ./init/main.c |
| cpu_idle () | ./init/main.c |

