
## 中断的生命周期

### Linux的中断处理过程

- 中断触发
  - 硬件相关过程：外设→中断控制器→处理器
- 硬中断处理
  - 关中断状态下快速的处理过程，“上半部”
- 软中断处理
  - 开中断状态下，完成庞杂的“下半部”
- 中断返回

### 以网络收包为例—中断触发

- 网卡
  - 收到一个网络包，根据接收描述符的指示，DMA写内存
  - 接收描述符中有中断位，在更新完描述符状态后发出中断
- 中断控制器
  - 收到中断信号，存到状态寄存器中
  - 根据中断使能情况，往处理器传递中断信号
- 处理器
  - 到达中断输入引脚，送到CP0_STATUS.IP域
  - 根据MASK、IE以及EXL/ERL，确定是否处理该中断
  - 如是，则将某条指令带上外部中断的信息，在提交时触发异常
  - 保存PC到EPC，切换到EXL状态，跳到0x80000180

### 以网络收包为例—硬中断(1)

- 通用例外入口(180)
  - 取出Cause，从例外处理函数列表加载处理函数的指针
- 外部中断入口
  - 保存进程上下文到内核栈
  - 关IE，清EXL，切换到内核模式
  - 转到平台相关处理
- 平台相关中断分发
  - 读中断状态，算中断号
- do_IRQ
  - 设置硬中断标记
  - 调用挂载在对应中断号的处理程序
  - 退出硬中断，检查并处理软中断

```
except_vec3_generic
PTR_L k0, exception_handlers(k1)
jr k0
handle_int
SAVE_ALL
CLI
...
PTR_LA ra, ret_from_irq
j plat_irq_dispatch
plat_irq_dispatch
if (pending & CAUSE_IP)
do_IRQ(ffs(intstatus));
do_IRQ
irq_enter();
generic_handle_irq(irq);
irq_exit();//invoke_softirq();
```

### 以网络收包为例—硬中断(2)

- 网卡的中断处理
  - 读网卡寄存器，确定需要处理的事件
  - 关闭网卡中断使能，避免大量网络包引起频繁中断
  - 通知NAPI有新任务

```
status = priv->hw->dma->dma_interrupt((void *) priv->dev->base_addr, &priv->xstats);
if (likely(status == handle_tx_rx))
    _stmmac_schedule(priv);
```

```
static inline void _stmmac_schedule(struct stmmac_priv *priv)
{
    if (likely(stmmac_has_work(priv))) {
        stmmac_disable_irq(priv);
        napi_schedule(&priv->napi);
    }
}
```

### 以网络收包为例—软中断

- 通过软件优化，提高系统响应速度
  - 在开中断状态下运行
  - 处理硬中断期间所设置的处理任务
  - 内核中预定义了10种软中断，一般驱动只能用基于软中断实现的tasklet机制

```
void irq_exit(void) {
    if (!in_interrupt() && local_softirq_pending())
        invoke_softirq();
}
static int stmmac_poll(struct napi_struct *napi, int budget)
{
    ...
    stmmac_tx(priv);
    work_done = stmmac_rx(priv, budget);
    if (work_done < budget) {
        napi_complete(napi);
        stmmac_enable_irq(priv);
    }
    return work_done;
}
```

### 中断返回

- 恢复上下文，执行eret指令
- ret_from_irq
  - resume_kernel
    - 如果可抢占，则尝试调度
    - 否则restore_all...eret
  - resume_userspace
    - 检查是否有待办事项（有抢占需求、有回调函数等）
    - 否则restore_all...eret

## 系统调用过程

### 系统调用简介

- 内核给用户程序提供的子程序
  - 进程控制：fork, clone, execve, exit, getpid, pause, wait
  - 文件操作：create, open, close, read, write, access, chdir, chmod
  - 系统控制：ioctl, ioperm, gettimeofday
  - 内存管理：brk, mmap, sync
  - 网络管理：gethostname, socket, connect, send
  - 用户管理：getuid, getgid
  - 进程间通信：signal, msgsnd, pipe, semctl, shmctl
  - 用strace命令可以跟踪一个进程的系统调用
- 两个基本要求
  - 安全性：内核态下运行，所有参数都应检查，避免受攻击
  - 兼容性：避免改应用，保护生态

![](img/0d16039e8c3308af077d6d25bb4413a8_312_0.png)

### 系统调用过程

- 与函数调用类似，Linux同时支持多种ABI
  - Syscall ID: O32(4000~4999), N32(5000~5999), N64(6000~6999)

| Register | use on input | use on output | Note |
|---|---|---|---|
| at | — | (caller saved) | |
| v0 | syscall number | return value | |
| v1 | — | 2nd fd only for pipe(2) | |
| a0~a2 | syscall arguments | returned unmodified | O32 |
| a0~a2, a4~a7 | syscall arguments | returned unmodified | N32 and 64 |
| a3 | 4th syscall argument | a3 set to 0/1 for success/error | |
| t0~t9 | — | (caller saved) | |
| s0~s8 | — | (callee saved) | |
| hi, lo | — | (caller saved) | |

- syscall指令
- 通用例外入口(0x80000180)
- excode=0x08, handle_sys
- SAVE_SOME, 切换至线程的内核栈，保存v*/a*/SR/CR
- 根据系统调用号跳到相应的服务函数
- RESTORE_SOME
- RESTORE_SP_AND_ERET

## 同步与通讯

- 现代操作系统的关键特性：多任务
- 当同一块数据被多段代码并发访问时需要同步
- 并发访问可能来自
  - 多处理器系统中同时运行的多个代码块
  - 由于中断引起的并发代码段
  - 由于线程调度引起的多线程并发执行
- 多数代码隐含原子性实现的假定
  - 读-改-写
  - 队列插入、删除
  - 红黑树插入、删除

### 基于锁的同步

- 将可能并发访问同一块数据的代码定义为临界区
- 进入临界区前先申请锁（并加锁）
- 申请失败者被阻塞
- 持有锁的线程离开临界区后释放锁
- 锁的类型
  - 自旋锁：循环等待直至得到锁
  - 互斥锁：如果加锁失败则休眠等待
  - 读写锁：允许有多个读或者一个写

```
selfspin:
ll      t0, lock
bnez    t0, selfspin
nop
li      t1, 0x1
sc      t1, lock
beqz    t1, selfspin
nop
<Critical section>
sw      zero, lock
```
