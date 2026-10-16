
## 软件体系结构
Software Architecture

张莉
北京航空航天大学
软件工程研究所
lily@buaa.edu.cn

### 张莉 教授，博士生导师

- 主要研究方向：智能化软件工程、软件体系结构、需求工程、系统建模和模型驱动方法、经验软件工程。

### 我们是可以互为师生。

> “孔子曰：‘三人行，必有我师。’ 是故弟子不必不如师，师不必贤于弟子。闻道有先后，术业有专攻，如是而已。”
> ——韩愈《师说》

- 教学内容
- 参考资料
- 学习方法
- 考试方法

### 学什么？

### 如何学？

### 学习的结果？

每年的教学内容会更新，作业可能不同。

## 什么是软件体系结构？

![](img/da691714eec1b93795825838a75ee408_49_0.png)

## 调查

- 你的背景
    - 你开发过的最大项目（代码、模块、人数）
    - 你对软件体系结构的理解
- 你的期望
    - 你期望的收获

## 《写了100W行的代码是啥感觉？》

我估计写到20万的时候就会突然有个疑问——“咦？我的头发呢？”

### 为啥问？

A同学：

我写两千行代码功能都像修理个两三天，一百万行真的是好多啊，最多了五年写了也就20-30万行代码左右。还是有任务在身的

B同学：

我是觉得如果说你一个工作写了一百万行代码，那你在公司的地位应该算资深员工了。如果你一个项目写了一百万行，那肯定是参与了一个比较大的项目了。如果你一个类写了一百万行，请问你用的是什么编辑器？如果你一个方法写了一百万行代码的话，请问你有没有被同事打死？

![](img/da691714eec1b93795825838a75ee408_51_0.png)

- 雷军说：“必须写够十万行代码，不要心存侥幸。没有写过足够代码量的，想成为高手是不可能的，只能纸上谈兵！”
- 大家觉得什么项目可以达到10万行代码？
- 前几年和华为合作，要求测试系统代码行数超过100万行
- 才发现工业界很多系统过100万行，不再是以前的少数。

## 代码规模

- Linux内核，早期几十万，后来100多万。
- Linux 2.6.23版本，源代码总行数大概为858万行，严格计算应该在550万行左右。
- Linux在2.6.18就超过1000万行了。也有说，Linux版本2.6.27更新后，已经超过了1000万行，但精确计算应该是600万行。
- 标准Linux-2.6.36.4内核，共13422535行代码。

## Linux 的代码规模

Linux版本2.6.27更新后，已经超过了1000万行。使用David Wheeler的SLOCCount计数程序对Linux内核代码库进行的分析发现了一些有趣的事实。分析发现只有6,399,191行源代码，因为这个计数程序没有计算空白行、注释和其它输入的信息。下面是SLOCCount程序提供的代码分类统计：

| 类型 | 行数 | 百分比 |
|---|---|---|
| 驱动程序 | 3,301,081 | 51.6 |
| 架构 | 1,258,638 | 19.7 |
| 文件系统 | 544,871 | 8.5 |
| 网络 | 376,716 | 5.9 |
| 声音 | 356,180 | 5.6 |
| Include | 320,078 | 5.0 |
| 内核 | 74,503 | 1.2 |
| 内存管理 | 36,312 | 0.6 |
| 密码学 | 32,769 | 0.5 |
| 安全 | 25,303 | 0.4 |
| 其它 | 72,780 | 1.1 |

### 标准Linux-2.6.36.4内核，共13422535行代码

| 子目录 | 行数 | 描述 |
|---|---|---|
| arch | 2670350 | 包含了所有体系结构相关的代码。对内核支持的每种处理器体系结构，都有一个独立的子目录。 |
| samples | 1947 | 和内核相关的一些范例代码。 |
| mm | 76437 | 高层的内存管理代码。与具体硬件体系结构相关的内存管理代码位于arch/*/mm目录下。 |
| sound | 624630 | 声卡的驱动程序。因为有许多针对各种不同总线的设备，该目录包含了某些总线相关的子目录，其中包含了对应的驱动程序的源代码。 |
| usr | 965 | 使用initramfs相关代码。 |
| security | 55282 | 安全框架和密钥管理。 |
| block | 18896 | 部分块设备驱动程序。 |
| virt | 5386 | Linux虚拟技术相关代码。 |
| Documentation | 354763 | 内核各方面的文档。 |
| include | 436665 | 包括编译内核所需要的大部分头文件。 |
| lib | 38783 | 包含了核心的库代码，与处理器结构相关的库代码放在arch/*/lib目录下。 |
| fs | 975380 | 所有文件系统实现的源代码。 |
| drivers | 7050171 | 设备驱动程序，每个不同的驱动占用一个子目录。 |
| firmware | 119682 | Linux下允许加载的第三方固件的代码。 |
| tools | 51976 | 一些测试程序。 |
| ipc | 7796 | 进程间通信的代码。 |
| net | 634073 | 包含了网络实现的代码，分为两部分，一个核心部分，另一部分用于实现各种网络协议。 |
| init | 4365 | 内核初始化代码（注意不是系统引导代码）。 |
| scripts | 65851 | 包含了编译内核或进行其他任务所需的所有脚本和实用程序。 |
| kernel | 167316 | 内核的核心部分，包括进程调度、定时器等。和硬件体系结构相关的一部分代码放在arch/*/kernel目录下，除非绝对必要，否则不要向该目录添加内容；凡修改该目录中文件的补丁，都会被极端谨慎地处理。 |
| crypto | 48615 | 包含了各种加密算法的实现。 |

## Windows 代码规模

- Windows 95只有1500万行代码，Windows 98有1800万行代码，Windows XP有3500万行代码，Windows Vista则达到了5000万行代码。Windows 7 大约5000万行左右；
- Google Chrome 100万行。金山的WPS代码行数约有150万行。
- Windows 7操作系统的技术研发人员总数约为2000人左右，他们又分为25个工作小组，每个小组成员总数约为100人左右，其中代码开发者40人，技术测试员40人，项目管理人员20人。（2000名开发人员和500名经理）
- Windows 8：35个开发团队
- 2018年3月，解散了Windows工程师团队。宣布了微软的部门重组，云计算和先进人工智能将成为微软的中心任务。

## 2019年同学们作业找到的大型开源项目

| 项目名称 | 项目出处 | 系统介绍 | 代码行数（万） |
|---|---|---|---|
| MeeGo | 诺基亚和英特尔合作 | MeeGo是英特尔和诺基亚合作推出的一个操作系统，在2010年巴塞罗那举办的世界移动通信大会上首次发布。 | 6712 |
| NetBSD | Chris Demetriou, Theo de Raadt, Adam Glass等 | NetBSD是一个完全开放源代码的类UNIX系统。NetBSD支持非常多的硬件架构，包括ia64、Macintosh、i386等。 | 3299 |
| asuswrt-merlin | RMerlin | Asuswrt-Merlin is an enhanced version of Asuswrt, the firmware used by Asus's modern routers. | 3075 |
| chromium | Google | Chromium是Google Chrome背后的开源项目。它基于其他开源软件项目（包括WebKit和Mozilla）的组件构成。 | 2467 |
| VoltDB | VoltDB Inc. | VoltDB是一种实时高性能内存中列式SQL RDBMS，专为海量实时一致性、高吞吐量和低延迟的应用程序设计。 | 2393 |
| Waterfox | Alex Kontos | Waterfox是一款基于Mozilla Firefox开发的第三方开放代码网页浏览器，适用于64位Microsoft Windows、macOS和Linux。 | 1779 |
| TrueOS | iXsystems | TrueOS是一个类Unix的、面向服务器的操作系统，基于FreeBSD-CURRENT的最新版本。 | 1695 |
| FreeBSD | 基于BSD Unix的源代码衍生而来的 | FreeBSD is an operating system used to power modern servers, desktops, and embedded platforms. | 1673 |
| OpenBSD | OpenBSD Foundation | OpenBSD起源于加拿大，由于Theo de Raadt对NetBSD开发过程中的一些意见不统一，愤而开创OpenBSD。 | 1308 |
| Boot To Gecko Firefox |  | Boot to Gecko 是 Firefox OS 操作系统的工程代号，是由Mozilla内部的一个工程师团队和Mozilla开源社区的共同努力完成的。 | 1303 |
| Unreal Engine | Epic Games | Unreal Engine，是Epic Games公司发行的一款开源游戏引擎，广泛应用于电脑游戏、虚拟现实和电影特效。 | 1244 |
| JetBrains MPS |  | JetBrains MPS使用完整的开发环境设计自己的领域特定语言。只需单击一下，即可获得完成、语义和类的支持。 | 1026 |
| Stellarium | GPL | Stellarium是一款免费开源的GPL（自由软件基金会GNU通用公共许可证）软件，它使用OpenGL模拟天文望远镜的功能。 | 1004 |
| TrinityCore | shinDarth | TrinityCore is an MMORPG framework that's built using C++, and using a back-end of MySQL for the DB content. | 1003 |
| Solaris | SUN | SUN公司开发的开源操作系统，目前在SUN公司被收购了之后已经停止维护。 | 987 |
| VirtualBox | ORACLE公司 | VirtualBox是一款开源虚拟机软件。VirtualBox就是一款免费的虚拟机软件，它不仅具有丰富的特色，而且性能也很优异。它简单易用，可虚拟的系统包括Windows、Linux、Mac OS X、OpenBSD、Solaris、IBM OS/2甚至Android等操作系统。 | 962 |
| Mono | Xamarin | Mono是一个由Xamarin公司（先前是Novell，最早为Ximian）所主导的自由开源软件项目。该项目的目标是创建一个Microsoft .NET Framework兼容的工具集。 | 918 |
| ArangoDB | ArangoDB GmbH | ArangoDB是ArangoDB GmbH开发的原生多模型数据库系统。数据库系统支持三种数据模型（键/值、文档、图）。 | 917 |
| LVS | 阿里巴巴。本项目在1998年5月由章文嵩博士发起 | LVS是Linux Virtual Server的简称，是一个虚拟的服务器集群系统。 | 890 |
| ali-kernel | 阿里巴巴 | Linux内核的阿里巴巴定制版，基于RHEL6源代码，包含了阿里巴巴所需的一些更新和新功能。 | 857 |
| uClinux | Lineo | uClinux表示micro-control linux，即微控制器领域中的Linux系统，是Lineo公司的主打产品。 | 821 |
| OpenJDK | Oracle | OpenJDK是JDK的开放源代码版本。 | 804 |
| Bitrig | Bitrig开发团队基于OpenBSD的一个分支 | Bitrig是一个免费、快速、安全的、高度可移植的类Unix开源操作系统。 | 782 |
| RT-Thread | 中国开源社区 | RT-Thread是一个集实时操作系统（RTOS）内核、中间件组件和开发者社区于一体的技术平台，能够提供先进、灵活的实时操作系统开发能力，具有较小内核、稳定可靠、简单易用、高效低耗等特点。经过11年的累积发展，RT-Thread已经拥有一个国内最大的嵌入式开源社区，同时被广泛应用于能源、车载、医疗、消费电子等多个行业。 | 728 |
