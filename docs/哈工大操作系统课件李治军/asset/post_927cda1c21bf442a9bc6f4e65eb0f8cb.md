
## 两个线程的样子：两个TCB、两个栈、切换的PC在栈中

ThreadCreate的核心就是用程序做出这三样东西

Yield
Stack1
Stack2
Heap
Data
Code
100: 1
A()
{
  B();
}
C()
{
  D();
}
两个执行序列
ffff
0000

1000 → 100
...
TCB1
esp=1000

```
void ThreadCreate(A)
{
    TCB *tcb=malloc();
    *stack=malloc();
    *stack = A;//100
    tcb.esp=stack;
}
```

## 将所有的东西组合在一起......

```
void WebExplorer() //main()
{ ThreadCreate(GetData,URL, buffer); ...
while(1) Yield(); }
```

```
void GetData(char *URL, char *p) {
 连接URL;下载; Yield() ;... }
```

```
void ThreadCreate (func,arg1) {
 申请栈;申请TCB;func等入栈;关联TCB与栈;... }
```

```
void Yield() { 压入现场;esp放在当前TCB 中;Next() ;从下个TCB取出esp;弹栈切换线程; }
```

调度函数，对系统影响很大，如可优先调度show!

```
gcc -o explorer get.c yield.c ... 或 gcc get.c... -lthread
```

![](img/365fc74cce32b405409a65a7e8830bec_106_0.png)

■ GetData下载到文本时会调用Yield()...

![](img/365fc74cce32b405409a65a7e8830bec_106_1.png)

## 为什么说是用户级线程——Yield是用户程序

如果进程的某个线程进入内核并阻塞，则...

进程 1
线程 1
线程 n
线程Yield!
进程 2
用户
内核
进程 1
进程Schedule!
进程 2
硬件
P P P

GetData
连接URL发起请求；
等待网卡IO...
进程阻塞

Show
显示文本和链接；
...；

## 核心级线程

## 核心级线程和用户级线程区别，哪个快？

- ThreadCreate是系统调用，会进入内核，内核知道TCB

- gcc -o explorer explorer.c yield.c ...

- 内核级线程gcc -o explorer explorer.c...； ThreadCreate是系统调用； Yield()用户不可见，调度点由系统决定

进程 1

进程 2

用户

核心

线程 1

线程 n

硬件

线程IO, Schedule...

![](img/365fc74cce32b405409a65a7e8830bec_108_0.png)

## 操作系统
Operating Systems

## L11 内核级线程

## Kernel Threads

授课教师：李治军

lizhijun_os@hit.edu.cn

综合楼411室

## 开始核心级线程

进程 1

进程 2

用户

核心

线程 1

线程 n

硬件

多处理器

多核

CPU 1
Cache
MMU

CPU 2
Cache
MMU

CPU 1
CPU 2
Cache
MMU

线程IO, Schedule...

内核级线程对多核的支持怎么样？

## 和用户级相比，核心级线程有什么不同？

- ThreadCreate是系统调用，内核管理TCB，内核负责切换线程

- 如何让切换成型？- 内核栈，TCB

- 用户栈是否还要用？执行的代码仍然在用户态，还要进行函数调用

- 一个栈到一套栈；两个栈到两套栈

- TCB关联内核栈，那用户栈怎么办？

![](img/365fc74cce32b405409a65a7e8830bec_111_0.png)

![](img/365fc74cce32b405409a65a7e8830bec_111_1.png)

## 用户栈和内核栈之间的关联

![](img/365fc74cce32b405409a65a7e8830bec_112_0.png)

所有中断(时钟、外设、INT 指令)都引起上述切换

中断(硬件)又一次帮助了操作系统...

## 仍然是那个A(), B(), C(), D()...

```
100: A() {
    B();
    104: }
200: B() {
    read();
    204: }
300: read() {
    int 0x80;
    304: }
system_call:
    call sys_read;
1000:
2000: sys_read(){ }
```

用户栈

104
204

认真体会从内核返回
(中断返回)时的样子...

内核栈

SS: SP
EFLAGS
304
CS
1000

用户程序
内核程序

## 开始内核中的切换： switch_to

switch_to: 仍然是通过 TCB找到内核栈指针；然后通过ret切到某个内核程序；最后再用 CS:PC切换到用户程序

```
sys_read() {启动磁盘读;将自己变成阻塞;找到next;switch_to(cur, next);}
```

线程S
内核栈
SS: SP
EFLAGS
304
CS
1000
???
esp
TCB1
switch
线程T
内核栈
SS: SP
EFLAGS
PC=??
CS=??
????
esp
TCB2

## 回答上面的问号??, ???, ????...

```
100: A() { 线程S代码
    ...
    int 0x80;
    ...
2000: sys_read(){ }
```

```
500: C() { 线程T代码
    ...
interrupt:
    call sys_xxx;
3000:
4000: sys_xxx(){ }
```

- ??? : sys_read函数的某个地方

- ?? : interrupt之前的某个地方

- ??? : sys_xxx函数中的某个地方

最关键的地方来了：T创建时如何填写??, ????

- ?? 500, 函数C()的开始地址

- ????
- 一段能完成第二级返回的代码，一段包含iret的代码...

| SS: SP |
| EFLAGS |
| PC=?? |
| CS=?? |
| ???? |

![](img/365fc74cce32b405409a65a7e8830bec_115_0.png)

## 内核线程switch_to的五段论

```
中断入口：(进入切换)
push ds;... pusha;
mov ds, 内核段号; ...
call 中断处理
???:
```

```
switch_to: (内核栈切换)
TCB[cur].esp=%esp;
%esp=TCB[next].esp;
ret
```

```
S、T非同一进程：(地址切换)
要首先切换地址映射表;
TCB[cur].ldtr=%ldtr
%ldtr=TCB[next].ldtr
//内存管理
```

```
中断处理：(引发切换)
启动磁盘读或时钟中断;
schedule();
}//ret
```

```
中断出口：(二级切换)
popa;...; pop ds;
iret
```

```
schedule: next=..;
call switch_to;
}//ret
```

第一级切换

## ThreadCreate! 做成那个样子...

500: C() { 线程T代码 ...

```
void ThreadCreate(...)
{
    TCB tcb=get_free_page();
    *krlstack = ...;
    *userstack传入;
    填写两个stack;
    tcb.esp=krlstack;
    tcb.状态=就绪;
    tcb入队;
}
```

![](img/365fc74cce32b405409a65a7e8830bec_117_0.png)

## 用户级线程、核心级线程的对比

|  | 用户级线程 | 核心级线程 | 用户+核心级 |
|---|---|---|---|
| 实现模型 |  |  |  |
| 利用多核 | 差 | 好 | 好 |
| 并发度 | 低 | 高 | 高 |
| 代价 | 小 | 大 | 中 |
| 内核改动 | 无 | 大 | 大 |
| 用户灵活性 | 大 | 小 | 大 |

## 操作系统
Operating Systems

## L12 内核级线程实现

## Create Kernel Threads

授课教师：李治军      lizhijun_os@hit.edu.cn
综合楼411室
