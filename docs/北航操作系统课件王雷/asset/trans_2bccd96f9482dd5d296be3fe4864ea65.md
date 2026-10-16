

## Bakery Algorithm

Critical section for n processes

- 进入临界区前，进程会获得一个编号。持有最小编号的进程进入临界区。
- 如果进程 $P_i$ 和 $P_j$ 获得相同的编号，若 $i < j$，则 $P_i$ 优先服务；否则 $P_j$ 优先服务。
- 编号方案始终按枚举的递增顺序生成数字；即 1,2,3,3,3,3,4,5...

### Bakery Algorithm

- 记号 <= 字典序 (票号 #, 进程 id #)
  - $(a,b) < (c,d)$ 若 $a < c$ 或若 $a = c$ 且 $b < d$
  - $\max(a_0,\cdots,a_{n-1})$ 是一个数 $k$，使得 $k \ge a_i$ 对 $i = 0,\cdots,n-1$

- 共享数据

```
boolean choosing[n];
int number[n];
```

Data structures are initialized to false and 0 respectively

### Bakery Algorithm

```
do {
    choosing[i] = true;
    number[i] = max(number[0], number[1], ..., number[n - 1])+1;
    choosing[i] = false;
    for (j = 0; j < n; j++) {
        while (choosing[j]);
        while ((number[j] != 0) && ((number[j], j) < (number[i], i)));
    }
    critical section
    number[i] = 0;
    remainder section
```

## 信号量机制

- 1965年Dijkstra。P（S），V（S）操作。P、V分别是荷兰语的test(proberen)和increment(verhogen)
- 其基本思路是用一种新的变量类型（semaphore）
- 信号量只能通过初始化和两个标准的原语来访问——作为OS核心代码执行，不受进程调度的打断

## 经典信号量机制

```
P(S) :while S<=0 do skip
    S:=S-1;
```

```
V(S) :S:=S+1;
```

## 计数信号量

```
Semaphore(S)
{
    value : integer;
    L : list of process;
    while (S.value <= 0)
        block(S.L);
    end
}

procedure V(S)
{
    var S : semaphore;
    begin
        S.value := S.value + 1;
        if S.value <= 0 then wakeup(S.L);
    end
```

## 信号量的使用：

- 必须置一次且只能置一次初值
- 只能由 P、V 操作来改变

## 物理意义

- S.value为正时表示资源的个数
- S.value为负时表示等待进程的个数
- P操作分配资源
- V操作释放资源。

## 信号量机制的实现

- 原子性问题；
  - 关中断、TS指令等
- PCB链表形式。

## 补充练习

```
movl sem, %ecx
decl 0(%ecx)
js down_failed
......
down_failed: block
```

## 信号量的应用

- 互斥
  - 利用信号量实现进程互斥（S=1）
- 同步
  - 利用信号量实现进程同步（S=0）
- 描述前趋关系
  - 利用信号量实现描述前趋关系（S=0）

## 互斥

P(S)

临界区

V(S)

P(S)

临界区

V(S)

## 同步

P(S)

代码

代码

V(S)

## 前趋关系

![](img/861c0ad57b0249095c0356c9e5a83b26_411_0.png)

## 解题步骤：

- 分析问题，弄清楚同步关系；
- 设置信号量，说明其含义和初值；
- 写出程序描述。

## “信号量集”机制

Process A:    Process B:
P(Dmutex);    P(Emutex);
P(Emutex);    P(Dmutex);

Process A: P(Dmutex);
Process B: P(Emutex);
Process A: P(Emutex);
Process B: P(Dmutex);

## AND型信号量集机制

- 基本思想：将进程需要的所有共享资源一次全部分配给它；待该进程使用完后再一起释放。

```
SP(S1, S2, ...,Sn)
    if S1=>1 and ... and Sn=>1 then
        for I :=1 to n do
            Si := Si - 1; SV(S1, S2, ...,Sn)
        endfor
    else
        wait in Si;
    endif
    for I :=1 to n do
        Si := Si + 1;
        wake waited proces
    endfor
```

## 一般“信号量集”机制

- 一次需要N个某类临界资源时，就要进行N次wait操作一一低效又可能死锁
- 基本思想：在AND型信号量集的基础上进行扩充：进程对信号量Si的测试值为ti（用于信号量的判断，即Si >= ti，表示资源数量低于ti时，便不予分配），占用值为di（用于信号量的增减，即Si = Si - di和Si = Si + di）

```
SP(S1, t1, d1, ... , Sn, tn, dn)
if S1=>t1 and ... and Sn=>tn then
    for I :=1 to n do
        Si := Si - di;
    endfor
else
    wait in Si;
endif
SV(S1, d1, ... ,Sn, dn)
for I :=1 to n do
    Si := Si + di;
    wake waited proces
endfor
```

## P.V操作的优缺点

- 优点：
  - 简单，而且表达能力强（用P.V操作可解决任何同步互斥问题）
- 缺点：
  - 不够安全；P.V操作使用不当会出现死锁；遇到复杂同步互斥问题时实现复杂

## 管程 (Monitor)

- 用信号量可实现进程间的同步，但由于信号量的控制分布在整个程序中，其正确性分析很困难。管程是管理进程间同步的机制，它保证进程互斥地访问共享变量，并方便地阻塞和唤醒进程。管程可以以函数库的形式实现。相比之下，管程比信号量好控制。

## 管程的组成

- 为每个共享资源设立一个管程，由用户编写一一类似于“面向对象”的观点
- 局部控制变量：一组局部于管程的控制变量
- 操作原语：对控制变量和临界资源进行操作的一组原语过程（程序代码），是访问该管程的唯一途径。这些原语本身是互斥的，任一时刻只允许一个进程去调用，其余需要访问的进程就等待。
- 初始化代码：对控制变量进行初始化的代码

## 同步、互斥和条件变量

- 互斥
- 同步：wait和signal
- 条件变量(condition)

  - 每个表示一种等待原因，并不取具体数值——相当于每个原因对应一个队列
  - 同步操作原语：针对条件变量x，c.wait(x)将自己阻塞在x队列中；c.signal(x)将x队列中的一个进程唤醒
    - 若进程P唤醒进程Q，则可有两种执行方式：
      - P等待，直到执行Q离开管程或下一次等待。
      - Q进入Ready队列，直到执行P离开管程或下一次等待。

