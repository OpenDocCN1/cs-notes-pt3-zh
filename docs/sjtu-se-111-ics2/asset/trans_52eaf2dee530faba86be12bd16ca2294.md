

## 并发方法

- **进程**
  - 难以共享资源：易于避免非预期共享
  - 增加/移除客户端开销高
- **线程**
  - 易于共享资源：也许太容易了
  - 中等开销
  - 对调度策略控制不多
  - 调试困难：事件顺序不可重复
- **I/O 多路复用**
  - 繁琐且底层
  - 对调度完全控制
  - 开销非常低
  - 无法创建更细粒度的并发级别
  - 不能利用多核

## 进程的传统视图

- 进程 = 进程上下文 + 代码、数据和栈

![](img/9bd5f6161cb6607b56d2fb964d1b8794_838_0.png)

## 进程的替代视图

- 进程 = 线程 + 代码、数据和内核上下文

Thread (main thread)

Code and Data

stack

SP

brk

PC

0

shared libraries

run-time heap

read/write data

read-only code/data

Thread context:
Data registers
Condition codes
Stack pointer (SP)
Program counter (PC)

Kernel context:
VM structures
Descriptor table
brk pointer

## 具有多个线程的进程

- 可以将多个线程与一个进程关联
  - 每个线程都有自己的逻辑控制流（PC 值序列）
  - 每个线程共享相同的 **代码**、**数据** 和 **内核上下文**
  - 每个线程有自己的 **线程 id**（TID）

## 线程的逻辑视图

- 与进程关联的线程形成一组对等体
  - 不同于形成树层次结构的进程

Threads associated with process foo

Process hierarchy

![](img/9bd5f6161cb6607b56d2fb964d1b8794_842_0.png)

![](img/9bd5f6161cb6607b56d2fb964d1b8794_842_1.png)

## 基于线程设计的优缺点

- + 线程间易于 **共享** 数据结构
  - 例如，日志信息、文件缓存。
- + 线程比进程更 **高效**
- - **非预期共享** 可能引入难以重现的微妙错误！
  - 数据易于共享既是线程的最大优势，也是最大弱点
  - 难以知道哪些数据被共享以及哪些是私有的

## 线程化 C 程序中的共享变量

- C 程序中哪些变量是共享的或不共享的？
  - 线程的内存模型是什么？
  - 变量的实例如何映射到内存？
  - 有多少线程引用这些实例中的每一个？

## 线程内存模型

- 概念模型：
  - 每个线程在进程的上下文中运行。
  - 每个线程有自己独立的线程上下文
    - 线程 ID、栈、栈指针、程序计数器、条件码和通用寄存器
  - 所有线程共享剩余的进程上下文
    - 进程虚拟地址空间的代码、数据、堆和共享库段
    - 打开的文件和已安装的处理程序

## 共享变量分析

```c
#include "csapp.h"
#define N 2
void *thread(void *vargp);

char **pptr; /* global variable */
```

## 共享变量分析

```c
#include "csapp.h"
#define N 2
void *thread(void *vargp);

char **ptr;
/* global variable */

int main()
{
    int i;
    pthread_t tid;
    char *msgs[N] = {
        "Hello from foo",
        "Hello from bar"
    };

    ptr = msgs;
    for (i = 0; i < N; i++)
        Pthread_create(&tid, NULL, thread, (void *)i);
    Pthread_exit(NULL);
}
```

## 共享变量分析

```
21 void *thread(void *var gp)
22 {
23     int myid = (int)var gp;
24     static int cnt = 0;
25
26     printf("[ %d]:%s(cnt=%d)\n", myid, ptr[myid], ++cnt);
}
```

## 变量实例到内存的映射

- 全局变量
  - 定义：函数外部声明的变量
  - 虚拟内存包含任何全局变量的确切一个实例
- 局部变量
  - 定义：函数内部声明且不带 static 属性的变量
  - 每个线程栈包含每个局部变量的一个实例
- 局部静态变量
  - 定义：函数内部声明并带 static 属性的变量
  - 虚拟内存包含任何局部静态变量的确切一个实例。

