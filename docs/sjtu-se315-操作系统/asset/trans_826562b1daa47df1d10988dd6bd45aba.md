

## 缓冲
- 附加到链路的消息队列；以三种方式之一实现
  1. 零容量 – 0 条消息
     发送方必须等待接收方（握手）
  2. 有界容量 – *n* 条消息的有限长度
     链路满时发送方必须等待
  3. 无界容量 – 无限长度
     发送方永不等待

## IPC 系统示例 – WinXP
- 以本地过程调用 LPC 设施为中心的报文传递
  - 仅在同一系统上的进程之间工作
  - 使用端口（类似邮箱）来建立和维护通信通道

## 生产者-消费者问题
- *生产者* 进程产生的信息由 *消费者* 进程消费
  - *无界缓冲区* 对缓冲区的大小不设实际限制
  - *有界缓冲区* 假设缓冲区大小固定

## 有界缓冲区 – 共享内存解决方案
- 共享数据
```
#define BUFFER_SIZE 10
typedef struct {
  ...
} item;

item buffer[BUFFER_SIZE];
int in = 0;
int out = 0;
```
- 解决方案是正确的，但只能使用 BUFFER_SIZE-1 个元素

## 有界缓冲区 – 生产者
```
while (true) {
    /* Produce an item */
    while (((in + 1) % BUFFER_SIZE) == out)
        ;  /* do nothing -- no free buffers */
    buffer[in] = item;
    in = (in + 1) % BUFFER_SIZE;
}
```

## 有界缓冲区 – 消费者
```
while (true) {
    while (in == out)
        ; // do nothing -- nothing to consume

    // remove an item from the buffer
    item = buffer[out];
    out = (out + 1) % BUFFER_SIZE;
    return item;
}
```

## xv6 中 IPC 示例：管道 pipe.c
```
struct pipe {
  struct spinlock lock;
  char data[PIPESIZE];
  uint nread;      // number of bytes read
  uint nwrite;     // number of bytes written
  int readopen;    // read fd is still open
  int writeopen; // write fd is still open
};
```

```
int
pipewrite(struct pipe *p, char *addr, int n)
{
    int i;

    acquire(&p->lock);
    for(i = 0; i < n; i++){
        while(p->nwrite == p->nread + PIPESIZE){  //DOC: pipewrite-full
            if(p->readopen == 0 || proc->killed){
                release(&p->lock);
                return -1;
            }
            wakeup(&p->nread);
            sleep(&p->nwrite, &p->lock);  //DOC: pipewrite-sleep
        }
        p->data[p->nwrite++ % PIPESIZE] = addr[i];
    }
    wakeup(&p->nread);  //DOC: pipewrite-wakeup1
    release(&p->lock);
    return n;
}
```

```
int
piperead(struct pipe *p, char *addr, int n)
{
    int i;

    acquire(&p->lock);
    while(p->nread == p->nwrite && p->writeopen){  //DOC: pipe-empty
        if(proc->killed){
            release(&p->lock);
            return -1;
        }
        sleep(&p->nread, &p->lock); //DOC: piperead-sleep
    }
    for(i = 0; i < n; i++){  //DOC: piperead-copy
        if(p->nread == p->nwrite)
            break;
        addr[i] = p->data[p->nread++ % PIPESIZE];
    }
    wakeup(&p->nwrite); //DOC: piperead-wakeup
    release(&p->lock);
    return i;
}
```

## 客户端服务器系统中的通信
- 套接字
- 远程过程调用
- 远程方法调用 Java

## 中断、陷阱、系统调用

## 概念
- 系统调用
  - 用户程序可以请求操作系统服务
- 异常
  - 指非法程序行为
- 中断
  - 指由硬件设备生成的信号

## 要求
- 必须保存处理器的寄存器以便将来透明恢复
- 必须为在内核中执行而设置
- 必须选择内核开始执行的位置
- 必须能够检索有关事件的信息，例如系统调用参数
- 必须全部安全完成
- 必须保持用户进程和内核的隔离

