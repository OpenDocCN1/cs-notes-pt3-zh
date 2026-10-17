
## PowerTimer工具集

- 设计初期的性能/功耗分析
- "New methodology for early-stage, microarchitecture-level power–performance analysis of microprocessors"

![](img/0d16039e8c3308af077d6d25bb4413a8_857_0.png)

Block diagram of PowerTimer toolset.

## 用PowerTimer进行性能和功耗分析

- L1 数据Cache大小对性能的影响
  - 性能有所提高，但是功耗增加迅猛
- ROB大小对性能的影响
  - 对浮点有一定影响，对定点和TPC-C略微有所提升
  - 1.2到1.4时性能反而下降，说明增加了重排序指令的数目，也需要改进如分支预测器等资源

![](img/0d16039e8c3308af077d6d25bb4413a8_858_0.png)

![](img/0d16039e8c3308af077d6d25bb4413a8_858_1.png)

![](img/0d16039e8c3308af077d6d25bb4413a8_858_2.png)

## PowerTimer分析细分流水级的优劣

- 以每级流水的FO4延迟表示流水深度
- 细分流水级（降低FO4级数）可以提高主频
- 最优的FO4在20左右
- 64位的先行进位加法器多少FO4？

Table 1 Latencies for 19-FO4 design point.

Fetch latencies
| Latency parameters | Latency in cycles |
|---|---|
| NFA predictor | 1 |
| L2 I-cache | 11 |
| L3 cache (infinite) | 85 |
| I-TLB miss | 10 |
| L2 I-TLB miss | 50 |

Decode latencies
| Latency parameters | Latency in cycles |
|---|---|
| Multiple decode | 2 |
| Millicode decode | 2 |
| Expand string | 2 |
| Mispredict cycles | 3 |
| Register read | 1 |

Execution pipe latencies
| Latency parameters | Latency in cycles |
|---|---|
| Fix execute | 1 |
| Float execute | 4 |
| Branch execute | 1 |
| Float divide | 12 |
| Integer multiply | 7 |
| Integer divide | 35 |
| Retire delay | 2 |

Load/store latencies
| Latency parameters | Latency in cycles |
|---|---|
| L1 D-load | 3 |
| L2 D-load | 9 |
| L3 (data) | 77 |
| Load fault | 2 |
| D-TLB miss | 7 |
| L2 D-TLB miss | 50 |
| StoreQ forward | 4 |

![](img/0d16039e8c3308af077d6d25bb4413a8_859_0.png)

![](img/0d16039e8c3308af077d6d25bb4413a8_859_1.png)

## POWER7性能建模、验证和评价

- **POWER7的性能分析覆盖晶体管级、处理器核、到全系统级**
  - 不同精细度对应不同速度，M1模型
  - 处理器核的模型（core model）和巢的模型（nest model）

- 通过性能模拟和分析，POWER7的工程师对各种参数变化的影响进行排序，逐渐改进设计，一直到最终完成设计
  - 实践和认识的反复迭代

- 性能测试程序很重要
  - 规模小，速度快；而且要具有代表性

- 通过芯片上集成的性能监测单元（PMU）对硅后POWER7芯片进行测量，构造精确的CPI分解栈，对阻塞条件进行剖析
  - 又一轮从认识和实践的螺旋上升

## M1模型

- 详细的拍精确的处理器核和巢的模型，使用踪迹驱动
- **M1模型可以执行在不同的模式**
  - 第一种模式：建模单个核以及其相应的巢，其它处理器核关闭
  - 第二种模式：对一个处理器核以及详细的巢进行建模，其他N-1个简单核用于模拟产生对巢的活动，这样就可以模拟N路的系统
  - 第三种模式：不对处理器核进行详细建模，而是使用N个简单的驱动核，可以更快地模拟N路的系统
  - 第四种模式：和第二种模式类似，只是执行在确定性的Cache情况下，可以模拟没有数据共享的工作负载，例如SPEC CPU的rate

## POWER7多核和多芯片模拟办法

![](img/0d16039e8c3308af077d6d25bb4413a8_862_0.png)

Figure 2
Multicore multichip simulation methodology.

## 处理器核模型（core model）

- 处理器核的模型包括一个详细的拍精确模型，模拟流水线和乱序执行机制，包括队列的模拟、流水线堵塞情况，L1和L2 cache，虚实地址转换，取指令，和分支预测机制等。
- 在POWER7设计过程中，需要模拟上百项不同配置的设计，通过执行大量工作负载来得到相应的性能数据，用于帮助分析瓶颈和预测可能存在的问题及比较各种配置。这些输出存放在一个数据库中，用于比较的便利和保存设计的历史。
- 处理器核的模型实现了许多性能监测计数器（PMC），最后在硬件上实现这些性能计数器，用于模型的验证

## 巢模型（nest model）

- 巢是芯片或系统中除了处理器核的部分
  - 如芯片内的处理器核的互连、多片和互连形成系统
  - LLC的模拟，内存控制器的模拟
- 对每个源到目的传输实际的线和逻辑的延迟进行计算
  - 包括所有在路上由于队列缓存的延迟，通路上的仲裁器和缓冲器等共享资源冲突情况，
- 巢的模型能使得在设计过程进行高层次优化，如算法的选择、buffer的大小和关键路径上锁存器，以减少互连通路上的设计瓶颈

## 用于性能模型的性能验证程序

- IBM建立了上万个性能测试的程序（PVPs）
  - 包括低层的测试处理器核和巢的单元（cache和内存）测试程序，以及高层的测试所有处理器核和整个巢模型的测试程序
- 第一类小或中规模的性能测试程序
  - 处理器核测试主要通过执行汇编语言指令来完成，巢的测试主要通过简单“软核”所产生的load、store和取指令的总线请求驱动来完成；有些测试面向特定的设计特性，如分支预测器，采用特定的事件计数来衡量；其它测试程序是程序中小代码段的组合或者是编译器产生代码的组合，采用CPI衡量
  - 巢模型的测试，采用各种延迟和带宽的衡量指标来衡量

## 用于性能模型的性能验证程序

- 第二类用于芯片层面的测试
  - 来自各种应用和工作负载的长代码序列，主要来自于SPEC CPU2006基准测试程序和一些高性能计算的核心代码，这些长代码序列在芯片层面的RTL模型以及M1模型上运行
  - 性能测试结果衡量主要是CPI
- 第三类采用Awan硬件仿真加速器对全系统进行性能验证
  - Awan可以执行大的程序，用于全芯片的性能验证工作

## POWER7的性能验证方法

- 基于UltraPoint采样获得采样的指令序列，程序代码在硬件仿真加速器Awan上和M1拍精确的软件模型上执行，获得M1和M3性能数据，最后送到性能分析工具并进行比较

![](img/0d16039e8c3308af077d6d25bb4413a8_867_0.png)

## POWER7性能监测

- **POWER7中集成了PMU用于性能监测、负载行为特性分析和系统的代码特性分析，包括6个线程层面的PMC**
  - **PMC1-PMC4是可编程的**
  - **PMC5统计非停顿的指令数**
  - **PMC6统计非停顿的拍数**
  - 每个核还包括4个HPMC（hypervisor PMC）
- 处理器和指令层面的性能事件的数目多达530种
  - 失效率、单元利用率、线程平衡、冒险条件、地址转换相关失效、停滞原因分析、指令混合情况、L1指令和数据reload的原因，cache和内存的延迟
- 芯片级的PMU称为PMUlet
  - 用于统计内存带宽、总线利用率和I/O带宽

## CPI stack的分析方法

- POWER7能通过性能计数器来进行CPI的栈分解，即把CPI的时钟周期数分解并归类于什么原因引起的拍数

![](img/0d16039e8c3308af077d6d25bb4413a8_869_0.png)
