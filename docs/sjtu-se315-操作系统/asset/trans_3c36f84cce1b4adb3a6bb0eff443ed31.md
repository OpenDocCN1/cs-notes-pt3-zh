

## Bounded-Buffer – Producer

```
while (true) {
    /* Produce an item */
    while (((in = (in + 1) % BUFFER SIZE count)
            == out)
        ; /* do nothing -- no free buffers */
    buffer[in] = item;
    in = (in + 1) % BUFFER SIZE;
}
```

## Bounded Buffer – Consumer

```
while (true) {
    while (in == out)
        ; // do nothing -- nothing to consume

    // remove an item from the buffer
    item = buffer[out];
    out = (out + 1) % BUFFER SIZE;
    return item;
}
```

## Example of IPC in xv6: Pipe
(pipe.c)

```
12 struct pipe {
13   struct spinlock lock;
14   char data[PIPESIZE];
15   uint nread;     // number of bytes read
16   uint nwrite;    // number of bytes written
17   int readopen;   // read fd is still open
18   int writeopen;  // write fd is still open
19 };
```

```
77 int
78 pipewrite(struct pipe *p, char *addr, int n)
79 {
80     int i;
81
82     acquire(&p->lock);
83     for(i = 0; i < n; i++){
84         while(p->nwrite == p->nread + PIPESIZE){  //DOC: pipewrite-full
85             if(p->readopen == 0 || proc->killed){
86                 release(&p->lock);
87                 return -1;
88             }
89             wakeup(&p->nread);
90             sleep(&p->nwrite, &p->lock);  //DOC: pipewrite-sleep
91         }
92         p->data[p->nwrite++ % PIPESIZE] = addr[i];
93     }
94     wakeup(&p->nread);  //DOC: pipewrite-wakeup1
95     release(&p->lock);
96     return n;
97 }
```

```
99 int
100 piperead(struct pipe *p, char *addr, int n)
101 {
102     int i;
103
104     acquire(&p->lock);
105     while(p->nread == p->nwrite && p->writeopen){  //DOC: pipe-empty
106         if(proc->killed){
107             release(&p->lock);
108             return -1;
109         }
110         sleep(&p->nread, &p->lock); //DOC: piperead-sleep
111     }
112     for(i = 0; i < n; i++){  //DOC: piperead-copy
113         if(p->nread == p->nwrite)
114             break;
115         addr[i] = p->data[p->nread++ % PIPESIZE];
116     }
117     wakeup(&p->nwrite);  //DOC: piperead-wakeup
118     release(&p->lock);
119     return i;
120 }
```

## Interprocess Communication – Message Passing

- 用于进程间通信和同步其操作的机制
- 消息系统
  - 进程之间可以在不使用共享变量的情况下相互通信
- IPC 设施提供两个操作：
  - **send**(message) – 消息大小固定或可变
  - **receive**(message)

## Message Passing (Cont.)

- 如果 *P* 和 Q 希望通信，它们需要：
  - 在它们之间建立一个 *通信链路*
  - 通过 send/receive 交换消息
- 通信链路的实现
  - 物理的（例如，共享内存、硬件总线）
  - 逻辑的（例如，逻辑属性）

## Implementation Questions

- 链路是如何建立的？
- 一个链路能否关联到两个以上的进程？
- 通信进程的每对之间可以有多少条链路？
- 链路的容量是多少？
- 链路能够容纳的消息大小是固定的还是可变的？
- 链路是单向的还是双向的？

## Indirect Communication

- 消息被定向并从邮箱接收（也称为端口）
  - 每个邮箱都有一个唯一的 id
  - 进程只有在共享一个邮箱时才能通信

## Indirect Communication

- 通信链路的属性
  - 只有当进程共享一个公共邮箱时才建立链路
  - 一个链路可能与多个进程相关联
  - 每对进程可能共享多个通信链路
  - 链路可能是单向的或双向的

## Indirect Communication

- 操作
  - 创建一个新的邮箱
  - 通过邮箱发送和接收消息
  - 销毁一个邮箱
- 原语定义为：
  **send**(A, message) – 向邮箱 A 发送一条消息
  **receive**(A, message) – 从邮箱 A 接收一条消息

