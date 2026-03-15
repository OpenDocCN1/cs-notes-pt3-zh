# 分布式系统：第22讲：分布式文件系统 📂

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_1.png)

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_2.png)

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_3.png)

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_4.png)

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_6.png)

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_8.png)

在本节课中，我们将要学习分布式文件系统的基础知识，特别是网络文件系统（NFS）。我们将从文件系统的基本概念开始，逐步深入到NFS的架构、工作原理、接口以及它如何处理一致性和缓存等问题。

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_10.png)

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_11.png)

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_13.png)

---

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_15.png)

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_16.png)

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_17.png)

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_19.png)

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_21.png)

## 概述

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_23.png)

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_24.png)

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_26.png)

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_27.png)

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_28.png)

上一节我们介绍了内容分发网络和边缘计算。本节中，我们来看看分布式文件系统，这是一种允许多台计算机通过网络共享文件和存储资源的系统。我们将重点讨论NFS，这是一个在UNIX和Linux世界中广泛使用的分布式文件系统。

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_29.png)

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_31.png)

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_32.png)

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_33.png)

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_34.png)

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_35.png)

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_36.png)

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_37.png)

---

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_39.png)

## 文件系统基础

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_40.png)

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_41.png)

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_42.png)

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_44.png)

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_45.png)

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_47.png)

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_48.png)

文件是操作系统提供的一种抽象，它使用户能够方便地存储和访问数据。从技术上讲，文件是一个**命名的、逻辑上相关的数据集合**。

在典型的类UNIX文件系统（如Linux或macOS）中，文件被视为**字节序列**。操作系统不解释这些字节的内容，也不为文件附加语义含义。目录本身也是一种特殊类型的文件，它包含一个表格，列出了该目录下的所有文件。

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_50.png)

文件包含两种信息：
1.  **数据**：用户创建并存储在文件中的实际内容。
2.  **元数据**：关于数据的数据，用于帮助操作系统管理文件。

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_52.png)

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_54.png)

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_55.png)

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_56.png)

在UNIX系统中，元数据存储在一个称为 **inode（索引节点）** 的数据结构中。inode记录了诸如文件名、文件大小、时间戳、文件所有者以及指向文件数据块在磁盘上位置的索引等信息。

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_58.png)

---

## 分布式文件系统简介

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_60.png)

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_61.png)

分布式文件系统允许客户端机器访问存储在远程服务器上的文件，使其看起来就像访问本地文件一样。这里需要区分两个概念：
*   **文件服务**：服务器提供的接口（API），客户端通过它来访问数据。
*   **文件服务器**：实际运行文件服务并存储数据的机器。

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_63.png)

分布式文件系统通常采用两种模型来实现文件服务：

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_65.png)

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_67.png)

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_68.png)

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_70.png)

以下是两种主要模型：

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_71.png)

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_73.png)

1.  **远程访问模型**：文件始终存储在服务器上。客户端每次读写文件时，都需要向服务器发送RPC请求，服务器处理请求并返回响应。所有操作都是远程进行的。
    *   **公式表示**：`客户端请求 -> RPC调用 -> 服务器处理 -> 返回响应`

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_75.png)

2.  **上传/下载模型**：客户端首次访问文件时，会将整个文件下载到本地。后续的所有读写操作都在本地副本上进行。当文件关闭时，修改后的版本会被上传回服务器。
    *   **公式表示**：`客户端打开文件 -> 下载副本 -> 本地读写 -> 关闭文件 -> 上传回服务器`

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_77.png)

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_78.png)

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_79.png)

远程访问模型网络开销较大，但服务器管理简单；上传/下载模型本地操作快，但需要处理多客户端同时修改同一文件时的**一致性**问题。

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_81.png)

---

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_83.png)

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_84.png)

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_85.png)

## 有状态与无状态服务器

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_87.png)

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_88.png)

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_89.png)

服务器的设计对文件系统的行为和功能有重要影响：

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_91.png)

*   **无状态服务器**：服务器不记录任何关于客户端或文件访问状态的信息。每个客户端请求都必须包含处理所需的所有信息。这种设计使服务器更**容错**（崩溃后无状态丢失），但实现某些功能（如文件锁定）更复杂。
*   **有状态服务器**：服务器会跟踪哪些客户端打开了哪些文件等状态信息。这使得请求处理更高效（无需重复发送信息），并且更容易维护**一致性**和实现**文件锁定**等功能。

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_93.png)

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_94.png)

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_95.png)

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_97.png)

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_98.png)

---

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_100.png)

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_102.png)

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_104.png)

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_106.png)

## 网络文件系统案例研究

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_108.png)

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_110.png)

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_111.png)

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_112.png)

NFS是一个经典的分布式文件系统，采用标准的客户端-服务器架构。

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_113.png)

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_114.png)

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_115.png)

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_117.png)

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_118.png)

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_119.png)

### NFS架构

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_121.png)

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_122.png)

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_124.png)

用户应用程序通过系统调用访问文件。**虚拟文件系统层** 负责抽象不同文件系统（如本地ext4和远程NFS）的细节。当VFS层判断一个文件属于NFS时，它会将请求转发给 **NFS客户端**。

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_126.png)

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_128.png)

NFS客户端通过 **RPC调用** 将请求发送到 **NFS服务器**。服务器收到请求后，通过其本地文件系统访问实际存储在磁盘上的文件数据，然后将结果通过RPC返回给客户端。

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_130.png)

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_131.png)

```plaintext
用户应用 -> 系统调用 -> VFS层 -> NFS客户端 -> RPC -> NFS服务器 -> 本地文件系统 -> 磁盘
```

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_133.png)

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_134.png)

### NFS接口与版本差异

NFS通过一组预定义的RPC调用来提供文件服务，例如 `lookup`, `create`, `read`, `write` 等。

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_136.png)

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_137.png)

NFS版本3和版本4的一个关键区别在于对“有状态”的支持：
*   **NFS v3**：设计为**无状态**服务器。因此，它没有 `open` RPC调用。客户端打开文件时，实际上只进行 `lookup` 操作来检查文件权限和有效性。文件指针等状态信息由客户端维护，并在每次 `read`/`write` RPC调用时作为参数发送。
*   **NFS v4**：引入了**有状态**服务器。它支持 `open` RPC调用，服务器可以跟踪文件打开状态。此外，v4还支持**复合RPC**，允许将多个操作（如 `lookup`, `open`, `read`）批量在一个RPC请求中发送，以减少网络往返延迟。

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_139.png)

### 挂载协议

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_141.png)

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_142.png)

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_143.png)

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_144.png)

客户端通过**挂载协议**将服务器上的远程目录映射到本地文件系统树中的一个位置。这使得访问远程文件就像访问本地目录一样。

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_145.png)

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_146.png)

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_148.png)

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_149.png)

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_150.png)

例如，用户的主目录可能存储在一台中央服务器上。当用户登录到任何客户端机器时，该机器会使用挂载协议将用户的主目录“挂载”到本地，例如 `/home/username`。

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_152.png)

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_153.png)

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_154.png)

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_156.png)

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_157.png)

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_159.png)

NFS v3 不允许**传递性挂载**（即服务器A挂载了服务器B的目录，客户端不能通过挂载A来访问B的目录），这是出于安全考虑。NFS v4 允许此操作，但需要更复杂的信任和转发机制。

---

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_161.png)

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_162.png)

## 一致性与缓存

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_164.png)

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_165.png)

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_166.png)

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_167.png)

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_168.png)

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_169.png)

在本地文件系统中，一个进程对文件的写入会立即对其他进程可见（**UNIX语义**）。但在分布式文件系统中，由于缓存的存在，这很难保证。

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_171.png)

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_172.png)

考虑一个场景：客户端A修改了一个文件，但修改还停留在其本地缓存中，尚未写回服务器。此时，客户端B从服务器读取该文件，它将看到文件的旧版本。

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_174.png)

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_175.png)

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_176.png)

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_178.png)

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_180.png)

NFS提供非常弱的一致性保证：
*   客户端会在本地缓存文件和文件属性（元数据）。
*   文件数据的修改通常不会立即写回服务器。许多实现采用“每30秒刷新一次脏缓存”的策略。
*   文件属性的缓存时间较短（如3秒），之后客户端会向服务器查询以获取最新属性。

这意味着NFS的语义接近**会话语义**：在一个客户端会话（文件打开期间）内的修改可能对其他客户端不可见，直到文件关闭且更改同步到服务器。

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_182.png)

### 文件锁定

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_184.png)

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_185.png)

文件锁定是协调多进程/多机器访问共享文件的重要机制。NFS v3 由于是无状态设计，**无法在协议层面实现文件锁定**。这导致一些依赖锁定的应用（如某些邮件服务器将邮箱文件存储在NFS上）可能出现问题。

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_187.png)

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_188.png)

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_189.png)

NFS v4 成为有状态服务器后，增加了对文件锁定的支持，解决了这个问题。

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_191.png)

### 委托

NFS v4 引入了**委托**作为性能优化，它结合了上传/下载模型的思想。
*   当只有一个客户端访问某个文件时，服务器可以将该文件的“管理权”**委托**给该客户端。
*   客户端获得文件的本地主副本，后续读写操作都在本地进行，无需RPC调用。
*   当另一个客户端尝试访问同一文件时，服务器会**召回委托**，文件控制权返回服务器，系统回退到标准的远程访问RPC模式。

---

## 总结

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_193.png)

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_194.png)

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_196.png)

本节课中我们一起学习了分布式文件系统的基础知识，并以NFS为具体案例进行了深入探讨。我们了解了文件与元数据的概念、分布式文件服务的两种模型（远程访问与上传/下载）、有状态与无状态服务器的区别。我们详细分析了NFS的架构、RPC接口、挂载协议，并讨论了其在一致性、缓存和文件锁定方面面临的挑战及解决方案。NFS从v3到v4的演变，特别是向有状态设计的转变，是为了支持更丰富的功能（如锁定）和更好的性能优化（如委托）。理解这些原理是构建和使用可靠分布式存储系统的关键。