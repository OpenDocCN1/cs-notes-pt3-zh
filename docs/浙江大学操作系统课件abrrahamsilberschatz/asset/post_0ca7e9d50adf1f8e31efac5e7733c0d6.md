

## Fig 12.11 I/O Without a Unified Buffer Cache

![](img/ba81f478b8c7b785e80053d010189a68_523_0.png)

## Unified Buffer Cache

A unified buffer cache uses the same page cache to cache both memory-mapped pages and ordinary file system I/O. This has the benefit of avoiding double caching and it allows the virtual memory system to manage file-system data.

一个统一高速缓存器使用相同页缓存去缓冲内存映射页和普通文件系统I/O

![](img/ba81f478b8c7b785e80053d010189a68_524_0.png)

![](img/ba81f478b8c7b785e80053d010189a68_524_1.png)

## Fig 12.12 I/O Using a Unified Buffer Cache

memory-mapped I/O

I/O using
read() and write()

buffer cache

file system

## Fig 12.13 Various Disk-Caching Locations

![](img/ba81f478b8c7b785e80053d010189a68_526_0.png)

## 12.7 Recovery恢复

- **Consistency checker** – compares data in directory structure with data blocks on disk, and tries to fix inconsistencies.  
  一致性检查：比较目录结构中的数据和磁盘块中的数据，尝试着去修正不一致

- Use system programs to *back up* data from disk to another storage device（floppy disk, magnetic tape）.  
  应用系统程序来备份数据到其他的存储设备，软盘，磁带

- Recover lost file or disk by *restoring* data from backup.  
  通过从备份重建来恢复丢失的文件或磁盘

## 12.8 Log Structured File Systems 日志结构文件系统

- Log structured (or journaling) file systems record each update to the file system as a **transaction**. 日志结构文件系统记录每一次更新文件系统事务

- All transactions are written to a log. A transaction is considered **committed** once it is written to the log. However, the file system may not yet be updated. 所有的事务都被记录在log中，一个事务被认为是记录在log中的一个提交（委托），然而文件系统可能仍然没有更新。

- The transactions in the log are asynchronously written to the file system. When the file system is modified, the transaction is removed from the log. 日志中的事务异步写入文件系统，当文件系统被修改，这个事务从日志中删除。

- If the file system crashes, all remaining transactions in the log must still be performed. 如果文件系统崩溃，在日志所有保存事务仍然可执行（恢复）

## NFS (Cont.)

- Interconnected workstations viewed as a set of independent machines with independent file systems, which allows sharing among these file systems in a transparent manner.

互联工作站被认为是独立独立文件系统用的独立机器，它允许在一种透明的方式在这些文件系统之中共享

- A remote directory is mounted over a local file system directory. The mounted directory looks like an integral subtree of the local file system, replacing the subtree descending from the local directory.

一个远程的目录在一个本地的文件系统目录上被安装，安装的目录看起来像本地的文件系统的一棵不可分的子树，替换子树从本地目录递减。

## NFS (Cont.)

- NFS is designed to operate in a heterogeneous environment of different machines, operating systems, and network architectures; the NFS specifications independent of these media. NFS被设计在不同的机器、操作系统、网络结构的不同环境中运行;NFS 说明是独立于这些介质的。

- This independence is achieved through the use of RPC primitives built on top of an External Data Representation (XDR) protocol used between two implementation-independent interfaces.
  
  通过使用建立在 2 个实现独立接口之间使用了XDR 协议的RPC原语来完成这独立，

- The NFS specification distinguishes between the services provided by a mount mechanism and the actual remote-file-access services.
  
  在服务器之间NFS说明的区分是由安装机制和实际的远程文件访问服务提供的

## Three Independent File Systems

![](img/ba81f478b8c7b785e80053d010189a68_533_0.png)

## Mounting in NFS

![](img/ba81f478b8c7b785e80053d010189a68_534_0.png)

(a) Mounts

(b) Cascading mounts

## NFS Mount Protocol（NFS安装协议）

- Establishes initial logical connection between server and client.
  在服务器和客户端之间建立初始逻辑连接
- Mount operation includes name of remote directory to be mounted and name of server machine storing it.安装操作包括远程目录名字被安装并且存储它的服务器名字。
- Mount request is mapped to corresponding RPC and forwarded to mount server running on server machine.
  安装请求被映射到相应的 RPC 并且提交给在服务器上运行的安装服务程序。
- *Export list* – specifies local file systems that server exports for mounting, along with names of machines that are permitted to mount them.
  输出列表 - 指定那个服务器为安装输出的本地文件系统，与机器的名字一起那被允许安装他们。

