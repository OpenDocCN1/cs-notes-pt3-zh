

- 命名管道：一个服务器端与一个客户端进程间的通信通道；
- 类型分为：字节流，消息流（报文）；访问分为：单向读，单向写，双向；还有关于操作阻塞 (wait/nowait) 的设置。
- CreateNamedPipe在服务器端创建并返回一个命名管道句柄；
- ConnectNamedPipe在服务器端等待客户进程的请求；
- CallNamedPipe从管道客户进程建立与服务器的管道连接；
- ReadFile、WriteFile（用于阻塞方式）、ReadFileEx、WriteFileEx（用于非阻塞方式）用于命名管道的读写；

## 管道的问题

- 普通管道只能用于具有亲缘关系的进程之间，而命名管道使得无亲缘关系的进程间也可以采用。
- 管道的缓冲区是有限的。
- 管道所传送的是无格式的字节流，这就要求管道的读出方和写入方必须事先约定好数据的格式，比如多少字节算作一个消息（或命令、或记录）等等。

## 消息队列

- 消息队列（也叫做报文队列）克服了早期Unix通信机制的一些缺点。例如“信号”（能够传送的信息量有限）。
- 消息队列是一个内核常驻的消息链表。可以把消息看作一个记录，具有特定的格式以及特定的优先级。
- 对消息队列有适当特权的进程可以向其中按照一定的规则添加新消息；对消息队列有适当特权的进程则可以从消息队列中检索消息。

## 消息队列

- 消息队列是随内核持续的。
- 消息队列是随内核持续的，只有在内核重启或者显式删除一个消息队列时，该消息队列才会真正被删除。
- 目前的消息队列：
  - POSIX消息队列
  - System V消息队列
  - Windows NT的邮件槽。

## System V

- 消息队列(message queue)：每个message不定长，由类型(type)和正文(text)组成
- UNIX消息队列API
  - msgget依据用户给出的整数值key，创建新消息队列或打开现有消息队列，返回一个消息队列ID；
  - msgsnd发送消息；
  - msgrcv接收消息，可以指定消息类型；没有消息时，返回-1；
  - msgctl对消息队列进行控制，如删除消息队列；
- 通过指定多种消息类型，可以在一个消息队列中建立多个虚拟信道

## Windows NT

- 邮件槽(mailslot)：驻留在OS核心，不定长数据块（报文），不可靠传递
- 通常采用client-server模式：单向的，从client发往server；server负责创建邮件槽，它可从邮件槽中读消息；client可利用邮件槽的名字向它发送消息；

## 有关的API

- CreateMailSlot服务器方创建邮件槽，返回其句柄；
- GetMailSlotInfo服务器查询邮件槽的信息，如：消息长度、消息数目、读操作等待时限等；
- SetMailSlotInfo服务器设置读操作等待时限；
- ReadFile服务器读邮件槽；
- CreateFile客户端打开邮件槽；
- WriteFile客户端发送消息；

## 共享内存

- 共享内存是最有用的进程间通信方式，它是最快的 IPC 形式（因为它避免了其它形式的 IPC 必须执行的开销巨大的缓冲复制）。
- 两个不同进程 A、B 共享内存的意义是，同一块物理内存被映射到进程 A、B 各自的进程地址空间。
- 当多个进程共享同一块内存区域，则需要同步机制约束（互斥锁和信号量都可以）。
- 共享内存通信的效率高（因为进程可以直接读写内存）。
- 进程之间在共享内存时，保持共享区域直到通信完毕。

## System V

- 进程间需要共享的数据被放在一个叫做IPC共享内存区域的地方。所有需要访问该共享区域的进程都要把该共享区域映射到本进程的地址空间中去。
- System V共享内存通过shmget获得或创建一个IPC共享内存区域，并返回相应的标识符。
- 内核在保证shmget获得或创建一个共享内存区，初始化该共享内存区相应的shmid_kernel结构体的同时，还将在特殊文件系统shm中，创建并打开一个同名文件，并在内存中建立起该文件的相应dentry及inode结构。
- 新打开的文件不属于任何一个进程（任何进程都可以访问该共享内存区）。所有这一切都是系统调用shmget完成的。

## System V的API

- `int shmget(key_t key, size_t size, int shmflg)`
- `void *shmat(int shmid, const void *shmaddr, int shmflg)`
- `int shmdt(const void *shmaddr)`
- `int shmctl(int shmid, int cmd, struct shmid_ds *buf)`

## POSIX

| Semaphores | Message Queues | Shared Memory |
|---|---|---|
| `sem_open` | `mq_open` | `shm_open` |
| `sem_close` | `mq_close` | `shm_unlink` |
| `sem_unlink` | `mq_unlink` |  |
| `sem_init` | `mq_getattr` |  |
| `sem_destroy` | `mq_setattr` |  |
| `sem_wait` | `mq_send` |  |
| `sem_trywait` | `mq_receive` |  |
| `sem_post` | `mq_notify` |  |
| `sem_getvalue` | `mq_getvalue` |  |

## UNIX中的文件映射

- **mmap**：建立进程地址空间到文件或共享存储区对象的映射，将文件偏移offset的字节映射到进程地址addr处：

  ```c
  caddr_t mmap(caddr_t addr, size_t len, int prot, int flags, int fildes, off_t off);
  ```

- **munmap**：拆除映射

  ```c
  int munmap(void *addr, size_t len);
  ```

- 优点：提高效率（消除不必要的数据拷贝）、降低复杂性（直接读写操作而不必管理缓冲区）、可直接将内存的数据类型记录在文件上（如指针）

## Windows NT的文件映射

- 采用文件映射(file mapping)机制：可以将整个文件映射为进程虚拟地址空间的一部分来加以访问。在 CreateFileMapping 和 OpenFileMapping 时可以指定对象名称。
- **CreateFileMapping**为指定文件创建一个文件映射对象，返回对象指针；
- **OpenFileMapping**打开一个命名的文件映射对象，返回对象指针；
- **MapViewOfFile**把文件映射到本进程的地址空间，返回映射地址空间的首地址；这时可利用首地址进行读写；
- **FlushViewOfFile**将映射地址空间的内容写到物理文件中；
- **UnmapViewOfFile**拆除文件映射与本进程地址空间间的映射关系；随后，可利用CloseHandle关闭文件映射对象；

![](img/861c0ad57b0249095c0356c9e5a83b26_600_0.png)

```
CreateFile

from system page file:
(HANDLE)0xffffffff

File Handle

CreateFileMapping

OpenFileMapping

File Mapping
Object Handle

MapViewOfFile()
```

## 注意

- 共享内存中的数据，从来不写入到实际磁盘文件中去（与mmap()映射普通文件实现的共享内存是不同的）。
- 共享内存机制是通过映射特殊文件系统shm中的文件实现的（特殊文件系统shm的安装点在交换分区上）。
- 共享内存是随内核持续的，除非显式删除共享内存。
- 应用接口和原理很简单，内部机制复杂。
- 为了实现更安全通信，往往还与信号量等同步机制共同使用。

