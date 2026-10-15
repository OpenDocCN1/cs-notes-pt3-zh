

## 系统调用

+   1. 从 IDT 中获取第 *n* 个描述符，其中 *n* 是 int 的参数。
+   2. 检查 %cs 中的 CPL 是否 <= 描述符中的 DPL，其中 DPL 为特权级。
+   3. 将 %esp 和 %ss 保存到 CPU 内部寄存器中，但仅当目标段选择符的 PL < CPL 时。
+   4. 从任务段描述符加载 %ss 和 %esp。
+   5. 压栈 %ss、%esp、%eflags、%cs、%eip，
+   6. 清除 %eflags 的某些位
+   7. 将 %cs 和 %eip 设置为描述符中的值

## 内核栈

![](img/53ee1e3b0eba43505c7d530851f32f6f_357_0.png)

Figure 3-1. Kernel stack after an int instruction.

## 中断

+   - 中断与系统调用类似，只是设备可以在任何时候产生它们
+   - 主板上有硬件来向 CPU 发信号，指示设备需要关注（例如，用户在键盘上输入了字符）
+   - 我们必须编程设备以产生中断，并安排 CPU 接收该中断。

```
17 void
18 tvinit(void)
19 {
20     int i;
21
22     for(i = 0; i < 256; i++)
23         SETGATE(idt[i], 0, SEG_KCODE<<3, vectors[i], 0);
24     SETGATE(idt[T_SYSCALL], 1, SEG_KCODE<<3, vectors[T_SYSCALL], DPL_USER);
25
26     initlock(&tickslock, "time");
27 }
```

```
213 #define SETGATE(gate, istrap, sel, off, d) \
214 {
215     (gate).off_15_0 = (uint)(off) & 0xffff; \
216     (gate).cs = (sel); \
217     (gate).args = 0; \
218     (gate).rsv1 = 0; \
219     (gate).type = (istrap) ? STS_TG32 : STS_IG32; \
220     (gate).s = 0; \
221     (gate).dpl = (d); \
222     (gate).p = 1; \
223     (gate).off_31_16 = (uint)(off) >> 16; \
224 }
```

![](img/53ee1e3b0eba43505c7d530851f32f6f_362_0.png)

## Intel 保留的 ID 编号

+   - 在 256 个可能的中断 ID 号中，Intel 将前 32 个保留为“异常”
+   - Linux 等操作系统可以自由使用剩余的 224 个可用中断 ID 号用于自己的目的（例如，来自外部设备的服务请求，或系统调用等其他目的）
+   - 示例：
+     - 0: 除法溢出故障
+     - 6: 未定义操作码
+     - 7: 协处理器不可用
+     - 11: 段不存在故障
+     - 12: 栈故障
+     - 13: 通用保护异常
+     - 14: 页故障异常

## CPU 的“取指-执行”周期

![](img/53ee1e3b0eba43505c7d530851f32f6f_364_0.png)

```
10 #define IO_TIMER1        0x040        // 8253 Timer #1
11
12 // Frequency of all three count-down timers;
13 // (TIMER_FREQ/freq) is the appropriate count
14 // to generate a frequency of freq Hz.
15
16 #define TIMER_FREQ       1193182
17 #define TIMER_DIV(x)     ((TIMER_FREQ+(x)/2)/(x))
18
19 #define TIMER_MODE       (IO_TIMER1 + 3) // timer mode port
20 #define TIMER_SEL0       0x00    // select counter 0
21 #define TIMER_RATEGEN    0x04    // mode 2, rate generator
22 #define TIMER_16BIT      0x30    // r/w counter 16 bits, LSB first
23
24 void
25 timerinit(void)
26 {
27     // Interrupt 100 times/sec.
28     outb(TIMER_MODE, TIMER_SEL0 | TIMER_RATEGEN | TIMER_16BIT);
29     outb(IO_TIMER1, TIMER_DIV(100) % 256);
30     outb(IO_TIMER1, TIMER_DIV(100) / 256);
31     picenable(IRQ_TIMER);
32 }
```

## 定时器中断

```
49 switch(tf->trapno){
50 case T_IRQ0 + IRQ_TIMER:
51     if(cpu->id == 0){
52         acquire(&tickslock);
53         ticks++;
54         wakeup(&ticks);
55         release(&tickslock);
56     }
57     lapiceoi();
58 break;
```

```
58 int
59 sys_sleep(void)
60 {
61     int n;
62     uint ticks0;
63     if(argint(0, &n) < 0)
64         return -1;
65     acquire(&tickslock);
66     ticks0 = ticks;
67     while(ticks - ticks0 < n){
68         if(proc->killed){
69             release(&tickslock);
70             return -1;
71         }
72         sleep(&ticks, &tickslock);
73     }
74     release(&tickslock);
75     return 0;
77 }
```

## 早期主板

+   - PIC（可编程中断控制器）
+     - picirq.c
+     - 8259A 芯片
+     - 每个 PIC 处理 8 个中断，并将它们复用到处理器的中断引脚上
+     - PIC 可以级联
+       - 主设备：0 到 7
+       - 从设备：8 到 15
+     - 阅读 timer.c 以了解定时器初始化
+   - XV6 在单处理器上工作正确

