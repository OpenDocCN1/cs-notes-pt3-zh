

## Other Considerations (Cont.)

- Program structure （程序结构）
  - `int A[][] = new int[1024][1024];`
  - Each row is stored in one page
  - Program 1
    ```
    for (j = 0; j < A.length; j++)
        for (i = 0; i < A.length; i++)
            A[i,j] = 0;
    ```
    1024 x 1024 page faults
  - Program 2
    ```
    for (i = 0; i < A.length; i++)
        for (j = 0; j < A.length; j++)
            A[i,j] = 0;
    ```
    1024 page faults

## Other Considerations (Cont.)

- I/O Interlock （I/O连接） – Pages must sometimes be locked into memory.
  有时页必须被锁进内存

- Consider I/O. Pages that are used for copying a file from a device must be locked from being selected for eviction by a page replacement algorithm.
  考虑I/O. 从一台设备拷贝一个文件被使用的页必须由页置换算法选择的淘汰被锁定。

## Reason Why Frames Used For I/O Must Be In Memory

![](img/ba81f478b8c7b785e80053d010189a68_474_0.png)

## Operating System Examples

- Windows NT
- Solaris 2

## Windows NT

- Uses demand paging with clustering. Clustering brings in pages surrounding the faulting page.
  用集群使用请求页。集群引入在缺页周边的页

- Processes are assigned working set minimum and working set maximum.
  进程被分配最小工作集合和最大工作集合。

- Working set minimum is the minimum number of pages the process is guaranteed to have in memory.
  最小工作集合是保证进程在内存中页的最小数目。

## WINDOWS NT

- A process may be assigned as many pages up to its working set maximum.
  进程可以被分配许多页，直到它的最大值工作集合

- When the amount of free memory in the system falls below a threshold, automatic working set trimming is performed to restore the amount of free memory.
  当系统的空闲内存数量在阈值下面时，自动工作集清理完成恢复一定数量空闲内存。

- Working set trimming removes pages from processes that have pages in excess of their working set minimum.
  工作集清理把超过最小工作集进程的页移开（减少页数目）。

## Solaris 2

- Maintains a list of free pages to assign faulting processes.
  维护空闲页表分配给缺页进程

- Lotsfree – threshold parameter to begin paging.
  Lotsfree-开始paging 的阈值

- Paging is peformed by _pageout_ process.
  paging 由_pageout_进程实现

- Pageout scans pages using modified clock algorithm.
  Pageout使用修改的CLOCK算法扫描页

- Scanrate is the rate at which pages are scanned. This ranged from slowscan to fastscan.
  Scanrate 是页被扫描率。这个范围是慢速扫描到快速扫描

- Pageout is called more frequently depending upon the amount of free memory available.
  Pageout 被调用频繁程度取决于可用空闲内存数目

## Chapter 12: File System Implementation 文件系统实现

- 12.1 File System Structure 文件系统结构
- 12.2 File System Implementation文件系统实现
- 12.3 Directory Implementation 目录实现
- 12.4 Allocation Methods 分派方法
- 12.5 Free-Space Management 空闲空间管理
- 12.6 Efficiency and Performance 效率和性能
- 12.7 Recovery 恢复
- 12.8 Log-Structured File Systems 日志结构文件系统
- 12.9 NFS 网络文件系统

### 12.1 File-System Structure
(文件系统结构)

- **File structure**（文件结构）
  - **Logical storage unit**（逻辑存储单元）
  - **Collection of related information**（相关信息的集合）
- **File system resides on secondary storage (disks).**
  （文件系统存在于辅助存储器中—磁盘）
- **File system organized into layers.**（文件系统按层组织）
- ***File control block* – storage structure consisting of information about a file.**
  （文件控制块FCB：由一个文件的相关信息组成的存储结构）

### Fig 12.1 Layered File System

application programs

logical file system

file-organization module

basic file system

I/O control

devices

### 12.2 File System Implementation 文件系统实现

#### 12.2.1 Overview

- The on-disk structures include:
  - Boot control block
  - Partition control block(分区控制块): superblock in UFS, Master File Table in NTFS
  - Directory structure
  - FCB

- In-memory structure include:
  - In-memory partition table
  - In-memory directory structure
  - System-wide open-file table
  - Per-process open-file table

### UNIX磁盘文件卷结构

| Sector # | 0 | 1 | inode | Data |
|---|---|---|---|---|
| | Boot Record | Super Block | Table | (File \& Directory) |

### Volume Structure in UNIX

- 超级块：描述文件系统的状态，包括磁盘空闲块栈，空闲i结点栈
- i节点（inode list）：存放文件说明信息，每项64字节
- 目录文件：每个目录项16字节。文件名区分大小写。

