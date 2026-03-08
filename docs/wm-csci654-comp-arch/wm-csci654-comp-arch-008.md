# 008：计算机体系结构模拟 2 🚀

![](img/f82727d71a2f1dd0a2eea62ed8aff0d1_1.png)

![](img/f82727d71a2f1dd0a2eea62ed8aff0d1_2.png)

![](img/f82727d71a2f1dd0a2eea62ed8aff0d1_4.png)

![](img/f82727d71a2f1dd0a2eea62ed8aff0d1_5.png)

![](img/f82727d71a2f1dd0a2eea62ed8aff0d1_7.png)

![](img/f82727d71a2f1dd0a2eea62ed8aff0d1_9.png)

在本节课中，我们将继续深入探讨计算机体系结构模拟，重点学习并行模拟引擎的实现原理、Akita模拟框架中的组件与端口设计，以及事件驱动与周期驱动模拟的差异与优化。

![](img/f82727d71a2f1dd0a2eea62ed8aff0d1_11.png)

![](img/f82727d71a2f1dd0a2eea62ed8aff0d1_13.png)

![](img/f82727d71a2f1dd0a2eea62ed8aff0d1_14.png)

![](img/f82727d71a2f1dd0a2eea62ed8aff0d1_15.png)

![](img/f82727d71a2f1dd0a2eea62ed8aff0d1_17.png)

## 概述

![](img/f82727d71a2f1dd0a2eea62ed8aff0d1_19.png)

![](img/f82727d71a2f1dd0a2eea62ed8aff0d1_20.png)

![](img/f82727d71a2f1dd0a2eea62ed8aff0d1_21.png)

![](img/f82727d71a2f1dd0a2eea62ed8aff0d1_22.png)

![](img/f82727d71a2f1dd0a2eea62ed8aff0d1_23.png)

上一节我们介绍了零引擎（Zero Engine）如何通过事件队列控制模拟的时序。本节中，我们将在此基础上，探讨如何实现并行模拟引擎，并深入了解Akita框架中组件、端口和连接的核心概念，最后初步接触“智能节拍”技术以优化模拟性能。

---

## 并行模拟引擎 🔄

![](img/f82727d71a2f1dd0a2eea62ed8aff0d1_25.png)

![](img/f82727d71a2f1dd0a2eea62ed8aff0d1_27.png)

在零引擎中，所有事件按时间顺序串行执行。然而，在数字电路中，许多组合逻辑可以在同一时钟周期内并行计算。因此，我们可以设计一个并行模拟引擎，让同一时刻调度的事件能够并行执行。

![](img/f82727d71a2f1dd0a2eea62ed8aff0d1_29.png)

![](img/f82727d71a2f1dd0a2eea62ed8aff0d1_31.png)

![](img/f82727d71a2f1dd0a2eea62ed8aff0d1_32.png)

![](img/f82727d71a2f1dd0a2eea62ed8aff0d1_34.png)

并行引擎遵循与零引擎相同的接口，包含五个核心方法。这样，从组件或用户的角度看，他们无需关心底层使用的是串行还是并行引擎，只需知道可以调度未来事件即可。

![](img/f82727d71a2f1dd0a2eea62ed8aff0d1_36.png)

![](img/f82727d71a2f1dd0a2eea62ed8aff0d1_37.png)

![](img/f82727d71a2f1dd0a2eea62ed8aff0d1_39.png)

### 并行引擎的工作原理

![](img/f82727d71a2f1dd0a2eea62ed8aff0d1_41.png)

![](img/f82727d71a2f1dd0a2eea62ed8aff0d1_43.png)

并行引擎的核心思想是：**将同一时刻（同一“轮次”）调度的事件分配到不同的线程中并行执行**。这被称为保守并行离散事件模拟，它保证了事件的时间顺序与串行模拟完全一致，从而确保了准确性，但可能会限制可扩展性。

![](img/f82727d71a2f1dd0a2eea62ed8aff0d1_45.png)

![](img/f82727d71a2f1dd0a2eea62ed8aff0d1_46.png)

以下是并行引擎运行一轮事件的关键代码逻辑概述：

![](img/f82727d71a2f1dd0a2eea62ed8aff0d1_48.png)

![](img/f82727d71a2f1dd0a2eea62ed8aff0d1_50.png)

![](img/f82727d71a2f1dd0a2eea62ed8aff0d1_51.png)

![](img/f82727d71a2f1dd0a2eea62ed8aff0d1_53.png)

```go
func (e *ParallelEngine) runRound(now akita.VTimeInSec) {
    // 1. 从队列池中取出所有队列，防止新事件在此期间被调度进来
    e.drainQChan()

    // 2. 并行执行当前时刻的所有事件
    var wg sync.WaitGroup
    for _, q := range e.queues {
        for event := q.Peek(); event != nil && event.Time() == now; event = q.Peek() {
            q.Pop()
            wg.Add(1)
            // 为每个事件启动一个协程（轻量级线程）执行
            go func(ev akita.Event) {
                e.runEventWithTempWorker(ev)
                wg.Done()
            }(event)
        }
        // 3. 将处理完的队列放回池中
        e.qChan <- q
    }
    // 4. 等待本轮所有事件执行完毕，再进入下一轮
    wg.Wait()
}
```

![](img/f82727d71a2f1dd0a2eea62ed8aff0d1_55.png)

![](img/f82727d71a2f1dd0a2eea62ed8aff0d1_57.png)

![](img/f82727d71a2f1dd0a2eea62ed8aff0d1_59.png)

**关键点**：
*   **队列池**：使用多个队列代替单一队列，避免调度事件成为全局性能瓶颈。
*   **协程**：利用Go语言的轻量级协程并行执行事件。
*   **同步**：通过 `sync.WaitGroup` 确保同一轮次的所有事件完成后，模拟时间才能向前推进。

---

![](img/f82727d71a2f1dd0a2eea62ed8aff0d1_61.png)

## 软件设计原则在Akita中的应用 🏗️

![](img/f82727d71a2f1dd0a2eea62ed8aff0d1_63.png)

![](img/f82727d71a2f1dd0a2eea62ed8aff0d1_65.png)

在构建像Akita这样复杂的模拟框架时，遵循良好的软件设计原则至关重要。这里我们重点介绍两个在Akita中广泛应用的原则。

![](img/f82727d71a2f1dd0a2eea62ed8aff0d1_67.png)

![](img/f82727d71a2f1dd0a2eea62ed8aff0d1_69.png)

![](img/f82727d71a2f1dd0a2eea62ed8aff0d1_71.png)

### 依赖倒置原则

![](img/f82727d71a2f1dd0a2eea62ed8aff0d1_73.png)

![](img/f82727d71a2f1dd0a2eea62ed8aff0d1_75.png)

![](img/f82727d71a2f1dd0a2eea62ed8aff0d1_77.png)

该原则要求：**高层模块不应依赖低层模块，二者都应依赖于抽象**。换句话说，要依赖于接口，而不是具体实现。

![](img/f82727d71a2f1dd0a2eea62ed8aff0d1_79.png)

**反面例子（硬依赖）**：
```go
type MyComponent struct {
    engine *ZeroEngine // 直接依赖具体的 ZeroEngine
}
```
如果未来想换成 `ParallelEngine`，就需要修改所有组件的代码。

![](img/f82727d71a2f1dd0a2eea62ed8aff0d1_81.png)

![](img/f82727d71a2f1dd0a2eea62ed8aff0d1_82.png)

**正确做法（依赖接口）**：
```go
type MyComponent struct {
    engine akita.Engine // 依赖抽象的 Engine 接口
}
```
`ZeroEngine` 和 `ParallelEngine` 都实现 `akita.Engine` 接口。这样，组件可以在运行时灵活配置使用哪种引擎，提高了代码的灵活性和可维护性。依赖方向从“组件 -> 具体引擎”转变为“组件 -> 抽象接口 <- 具体引擎”，实现了“倒置”。

![](img/f82727d71a2f1dd0a2eea62ed8aff0d1_84.png)

![](img/f82727d71a2f1dd0a2eea62ed8aff0d1_86.png)

![](img/f82727d71a2f1dd0a2eea62ed8aff0d1_88.png)

### 接口隔离原则

![](img/f82727d71a2f1dd0a2eea62ed8aff0d1_90.png)

![](img/f82727d71a2f1dd0a2eea62ed8aff0d1_92.png)

该原则要求：**不应强迫客户端依赖它们不使用的方法**。即，接口应该小而专一，而不是大而全。

![](img/f82727d71a2f1dd0a2eea62ed8aff0d1_94.png)

![](img/f82727d71a2f1dd0a2eea62ed8aff0d1_96.png)

![](img/f82727d71a2f1dd0a2eea62ed8aff0d1_98.png)

**潜在问题**：
组件通常只需要引擎的**调度**功能，但 `akita.Engine` 接口可能还包含 `Run()`, `Pause()` 等控制模拟流程的方法。这迫使组件依赖了它不需要的方法。

**优化方向**：
可以定义一个更精细的 `EventScheduler` 接口，只包含调度相关的方法。然后让 `Engine` 接口继承或实现 `EventScheduler`。这样，只需要调度功能的组件就可以只依赖 `EventScheduler` 接口。

![](img/f82727d71a2f1dd0a2eea62ed8aff0d1_100.png)

![](img/f82727d71a2f1dd0a2eea62ed8aff0d1_101.png)

---

![](img/f82727d71a2f1dd0a2eea62ed8aff0d1_103.png)

## Akita 模拟框架的核心元素 ⚙️

![](img/f82727d71a2f1dd0a2eea62ed8aff0d1_105.png)

![](img/f82727d71a2f1dd0a2eea62ed8aff0d1_107.png)

### 组件

![](img/f82727d71a2f1dd0a2eea62ed8aff0d1_109.png)

![](img/f82727d71a2f1dd0a2eea62ed8aff0d1_111.png)

![](img/f82727d71a2f1dd0a2eea62ed8aff0d1_113.png)

![](img/f82727d71a2f1dd0a2eea62ed8aff0d1_115.png)

组件是Akita模拟的基本构建块，可以代表CPU核、缓存、内存控制器等任何逻辑单元。在代码中，`Component` 是一个聚合了多个小接口的大接口。

![](img/f82727d71a2f1dd0a2eea62ed8aff0d1_117.png)

```go
type Component interface {
    Named                     // 具有名称
    Hookable                  // 可插入钩子函数
    PortOwner                 // 拥有端口
    Handler                   // 能处理事件
    NotifyRecv                // 能接收通知
}
```
这种设计本身就体现了**接口隔离原则**，允许用户只关注他们需要的部分功能。

![](img/f82727d71a2f1dd0a2eea62ed8aff0d1_119.png)

![](img/f82727d71a2f1dd0a2eea62ed8aff0d1_121.png)

![](img/f82727d71a2f1dd0a2eea62ed8aff0d1_123.png)

### 消息

![](img/f82727d71a2f1dd0a2eea62ed8aff0d1_125.png)

组件之间通过**消息**进行通信。消息携带需要传递的数据和元信息。

```go
type Msg interface {
    Meta() *MsgMeta          // 获取元数据（ID、源、目的、大小等）
    Clone() Msg              // 克隆消息（生成新ID）
}
```
**关键点**：
*   **唯一ID**：每条消息有唯一ID，用于追踪。
*   **单次使用**：消息被处理后即失效，如需重用必须克隆。
*   **元数据**：包含路由、计时所需的所有信息。

### 端口与连接

![](img/f82727d71a2f1dd0a2eea62ed8aff0d1_127.png)

![](img/f82727d71a2f1dd0a2eea62ed8aff0d1_129.png)

![](img/f82727d71a2f1dd0a2eea62ed8aff0d1_130.png)

端口是组件与外界通信的端点，内部包含输入和输出缓冲区。连接则像导线一样链接两个或多个端口。

![](img/f82727d71a2f1dd0a2eea62ed8aff0d1_132.png)

**端口的关键方法**：
*   `Send(msg)`：组件调用，将消息放入端口的**输出缓冲区**，并尝试通知连接。
*   `Deliver(msg)`：连接调用，将消息放入端口的**输入缓冲区**，并通知组件有消息到达。
*   `RetrieveIncoming()`：组件调用，从**输入缓冲区**取走消息进行处理。
*   `NotifyAvailable()`：当缓冲区状态变化（如从满变为非满）时，通知对方可以继续发送。

![](img/f82727d71a2f1dd0a2eea62ed8aff0d1_134.png)

**连接**：
*   一个连接可以关联多个端口。
*   一个端口只能属于一个连接。
*   连接负责在端口间搬运消息，可以模拟传输延迟。

---

![](img/f82727d71a2f1dd0a2eea62ed8aff0d1_136.png)

## 从事件驱动到周期驱动 ⏱️

![](img/f82727d71a2f1dd0a2eea62ed8aff0d1_138.png)

纯事件驱动模拟性能高，但开发复杂，需要处理各种事件类型和重试逻辑。周期驱动模拟（每个周期都调用组件的 `Tick()` 函数）逻辑简单，但性能较低，因为即使组件空闲也会“空转”。

![](img/f82727d71a2f1dd0a2eea62ed8aff0d1_140.png)

![](img/f82727d71a2f1dd0a2eea62ed8aff0d1_141.png)

![](img/f82727d71a2f1dd0a2eea62ed8aff0d1_143.png)

![](img/f82727d71a2f1dd0a2eea62ed8aff0d1_145.png)

![](img/f82727d71a2f1dd0a2eea62ed8aff0d1_147.png)

![](img/f82727d71a2f1dd0a2eea62ed8aff0d1_148.png)

### 智能节拍技术

![](img/f82727d71a2f1dd0a2eea62ed8aff0d1_150.png)

![](img/f82727d71a2f1dd0a2eea62ed8aff0d1_152.png)

![](img/f82727d71a2f1dd0a2eea62ed8aff0d1_154.png)

Akita引入了**智能节拍**技术，旨在结合两者的优点。其核心思想是：**让组件在需要工作时才被“唤醒”执行Tick**。

![](img/f82727d71a2f1dd0a2eea62ed8aff0d1_156.png)

**如何判断是否需要Tick？**
如果一个组件的 `Tick()` 执行后没有产生任何**进展**，那么这次Tick就是不必要的，可以跳过。进展包括：
1.  更新了内部状态。
2.  成功发送出一条消息。

![](img/f82727d71a2f1dd0a2eea62ed8aff0d1_158.png)

![](img/f82727d71a2f1dd0a2eea62ed8aff0d1_160.png)

**何时重新唤醒组件？**
当导致组件停滞的外部条件改变时，应重新调度Tick事件：
1.  **从空闲到有任务**：当端口的输入缓冲区有新消息到达时（`NotifyRecv` 被调用）。
2.  **从阻塞到可发送**：当端口的输出缓冲区从满变为非满时（`NotifyAvailable` 被调用）。

![](img/f82727d71a2f1dd0a2eea62ed8aff0d1_162.png)

![](img/f82727d71a2f1dd0a2eea62ed8aff0d1_164.png)

**智能Tick的组件Handle函数框架**：
```go
func (c *MyComponent) Handle(ev akita.Event) {
    switch e := ev.(type) {
    case *akita.TickEvent:
        madeProgress := c.Tick() // Tick函数返回本次是否取得进展
        if madeProgress {
            c.Schedule(c.NextTickTime()) // 有进展，继续调度下一次Tick
        }
        // 无进展，则不调度，组件进入“睡眠”
    }
}
```

![](img/f82727d71a2f1dd0a2eea62ed8aff0d1_166.png)

![](img/f82727d71a2f1dd0a2eea62ed8aff0d1_168.png)

![](img/f82727d71a2f1dd0a2eea62ed8aff0d1_170.png)

![](img/f82727d71a2f1dd0a2eea62ed8aff0d1_172.png)

![](img/f82727d71a2f1dd0a2eea62ed8aff0d1_174.png)

通过这种方式，组件在忙碌时像周期模拟一样连续工作，在空闲或阻塞时则自动跳过无用的周期，从而在保持开发简单性的同时，逼近事件驱动模拟的性能。

![](img/f82727d71a2f1dd0a2eea62ed8aff0d1_175.png)

![](img/f82727d71a2f1dd0a2eea62ed8aff0d1_176.png)

![](img/f82727d71a2f1dd0a2eea62ed8aff0d1_178.png)

---

![](img/f82727d71a2f1dd0a2eea62ed8aff0d1_180.png)

![](img/f82727d71a2f1dd0a2eea62ed8aff0d1_182.png)

## 总结

![](img/f82727d71a2f1dd0a2eea62ed8aff0d1_184.png)

![](img/f82727d71a2f1dd0a2eea62ed8aff0d1_186.png)

本节课我们一起深入学习了计算机体系结构模拟的进阶内容。

![](img/f82727d71a2f1dd0a2eea62ed8aff0d1_188.png)

![](img/f82727d71a2f1dd0a2eea62ed8aff0d1_190.png)

![](img/f82727d71a2f1dd0a2eea62ed8aff0d1_192.png)

![](img/f82727d71a2f1dd0a2eea62ed8aff0d1_194.png)

我们首先剖析了**并行模拟引擎**的实现，了解了如何利用多队列和协程让同一时刻的事件并行执行，同时通过保守策略保证时序正确性。

![](img/f82727d71a2f1dd0a2eea62ed8aff0d1_196.png)

![](img/f82727d71a2f1dd0a2eea62ed8aff0d1_198.png)

接着，我们探讨了**依赖倒置**和**接口隔离**这两个重要的软件设计原则在Akita框架中的应用，理解了它们如何提升代码的灵活性和可维护性。

![](img/f82727d71a2f1dd0a2eea62ed8aff0d1_200.png)

![](img/f82727d71a2f1dd0a2eea62ed8aff0d1_202.png)

然后，我们系统学习了Akita框架的三大核心元素：**组件**作为功能单元，**消息**作为通信载体，以及**端口与连接**构成的通信网络。我们通过一个Ping示例，直观展示了事件驱动的模拟流程。

![](img/f82727d71a2f1dd0a2eea62ed8aff0d1_204.png)

![](img/f82727d71a2f1dd0a2eea62ed8aff0d1_206.png)

![](img/f82727d71a2f1dd0a2eea62ed8aff0d1_208.png)

最后，我们指出了纯事件驱动模拟的复杂性，并引入了**智能节拍**这一混合技术。它通过让组件在“有进展时才Tick”的机制，巧妙地在周期驱动的易用性和事件驱动的高性能之间取得了平衡。

![](img/f82727d71a2f1dd0a2eea62ed8aff0d1_210.png)

![](img/f82727d71a2f1dd0a2eea62ed8aff0d1_211.png)

![](img/f82727d71a2f1dd0a2eea62ed8aff0d1_213.png)

![](img/f82727d71a2f1dd0a2eea62ed8aff0d1_215.png)

![](img/f82727d71a2f1dd0a2eea62ed8aff0d1_217.png)

在接下来的课程中，我们将继续探讨智能节拍的具体实现，并学习如何构建更复杂的模拟系统。