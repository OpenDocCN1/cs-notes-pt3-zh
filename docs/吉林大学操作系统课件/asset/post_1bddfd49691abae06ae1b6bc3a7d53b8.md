
## 13.5.3 文件结构

- 逻辑结构
  - 流式文件，字节序列
    - 读写命令中包含字节数
    - **read(fd,buf,count)**
      - 其中count为传输字节数
    - 模拟记录式文件
- 物理结构
  - 直接与间接
    - **0级，1级，2级，3级间接寻块**

## 13.5.4 文件目录与连接

- 目录项
  - 相当FCB次部
  - 形式为(文件名，文件号)
- Inode
  - 相当于FCB主部
  - 每个inode有一个i_number
  - 多个文件名对应同一个i_number（连接共享）

## 连接实现

![](img/7b6892715d0da57dced81602d7459e7e_909_0.png)

| 文件 | i_number |
|---|---:|
| f2 | 15 |

| 文件 | i_number |
|---|---:|
| f1 | 15 |

```
link("/users/wang/d1/f1", "/users/li/f2")
```

i_number=15

## 13.5.5 文件系统映射

read(4,...)

read(4,...)
...
write(2,...)

用户空间

u_ofile

u_ofile

file

i_node

系统空间

数据块

i_list

磁盘空间

![](img/7b6892715d0da57dced81602d7459e7e_910_0.png)

## 相关表目

### 1. u_ofile（每进程一个）

```
struct user
{
    ...
    int u_ofile[NOFILE];
    ...
}

#define NOFILE 15
```

### 2. file（系统一个）

```
struct file
{
    char f_flag;   //R,W,PIPE
    char f_count;
    int f_inode;
    char *f_offset[2];
}file[NFILE]

#define NFILE 100
```

## 相关表目

### 3 inode表(系统一个)

```
struct inode {
    int    i_flag;
    char   i_count;
    char   i_dev;
    char   i_number;
    char   i_mode;
    char   i_nlink;
    char   i_uid;
    char   i_gid;
    char   i_size0;
    char   *i_size1;
    int    i_addr[8];
    int    i_lastr;
} inode[NINODE];
```

表间联系：

u_ofile → file

(n)        (1)

file → inode

(n)        (1)

## 13.5.6 文件卷的安装

- **mount**：用一个文件卷的根目录取代一个已经存在的空目录节点

UNIX文件卷

![](img/7b6892715d0da57dced81602d7459e7e_913_0.png)

## 超级块结构（安装后读入内存，卸下时回写磁盘）

```
Struct filesys {
int s_isize;   //size in blocks of i list
int s_fsize;   //size in blocks of entire volume
int s_nfree;   //number of in core free blocks
int s_free[100];   //in core free blocks
int s_ninode;   //number of in core I list
int s_inode[100];   //in core free I nodes
char s_flock;   //free list locking
char s_ilock;   //i list locking
char s_fmod;   //super block modified flag
char s_ronly;   //mounted read only flag
char s_time[2];   //current date of last update
int pad[50];
}
```

## 13.5.7磁盘空间管理：

100个空闲块为一组，组之间相互链接。

![](img/7b6892715d0da57dced81602d7459e7e_916_0.png)

Super block
...
s_nfree=100
s_free[0]
s_free[1]
...
s_free[99]
...

特点：速度快，空间省。

## 13.5.8 空闲inode管理：

s_inode最多可以记载100个空闲inode(编号)

申请时：

- (1) s_ninode>0, 取s_inode[--s_ninode];
- (2) s_ninode=0, 由磁盘inode区顺取100个空闲I节点(i_nlink=0) 将其编号填入s_inode表中，修改s_ninode，然后分配。

释放时：

- (1) s_ninode<100, s_inode[s_ninode++]=i_number (释放的);
- (2) s_ninode=100, 丢弃。

## 13.5.9 快速文件系统

- 经典UNIX文件系统
  - Inode区与内容存储区相分离
    - 查找速度慢(引臂在inode区与块存储区之间往复移动，尤其长路径名)
  - 文件长度大于5120字节：间接寻块
  - 文件名长度14字节以内
- Fast File System (FFS)
  - 1984UC Berkeley
  - 被许多现代UNIX采用，包括4.3BSD
  - 效率提高一个数量级

## 13.5.9 快速文件系统

### 快速文件系统

- FFS将磁碟卷划分分为若干个柱面组(cylinder group)，每个柱面组占若干连续的柱面，作为相对独立的文件卷管理
- FFS采用较大的磁碟块以减少I/O间址并提高I/O效率 (达8KB)
- FFS打破了文件名称长度最多为14字节的限制，文件名称长度可达255字节
- FFS支持符号连接(symbolic link)，这种连接可以跨文件卷或主机

## 符号连接(symbolic link)

- 硬连接(hard link)局限性:
  - 只能连接普通文件
  - 不能跨文件卷
- 软连接(soft link)
  - 可以连接目录文件
  - 可以跨文件卷, 或主机

## 符号连接

d1/d2/d4/f1 是一已存在文件

```
link("d1/d2/d4/f1","d1/d2/d3/f2")
```

建立一个硬连接

```
ln -s d1/d2/d4 d5/s
```

建立一个软连接，s 的内容为 d1/d2/d4

d5/s/f1 为 i_number=15 的文件

```
以后执行 unlink("d1/d2/d4/f1")
```

d5/s/f1 自动失效

![](img/7b6892715d0da57dced81602d7459e7e_921_0.png)

## 13.5.9 快速文件系统

### UNIX 4.3BSD柱面组

|  |
|---|---|
| 数据块 |
| Super block |
| Cylinder block |
| Inode |
| 数据块 |

## 远程安装

client1

client2

server1

server2

![](img/7b6892715d0da57dced81602d7459e7e_924_0.png)

## NFS安装协议

- 建立client与server之间的初始联系
- 安装参数包括
  - 远程待安装目录
  - 服务器名
- 安装请求被映射为对应的RPC调用,并传给远程server
- 服务器端的export list指明可被安装目录列表,以及可对其执行安装操作的clients
