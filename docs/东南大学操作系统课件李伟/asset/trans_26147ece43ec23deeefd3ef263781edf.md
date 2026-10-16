

## 分层结构

- 操作系统被划分为若干层（级别），每一层都建立在较低层之上。最底层（第 0 层）是硬件；最高层（第 N 层）是用户界面。
- 借助模块化，各层被选择为每一层仅使用较低层的功能（操作）和服务

## 分层操作系统

![](img/0f9477f9dd9e571abf0b2ce4550a9e88_111_0.png)

## OS/2 层结构

![](img/0f9477f9dd9e571abf0b2ce4550a9e88_112_0.png)

### 微内核结构

- 将尽可能多的内容从内核移至 *“用户”* 空间
- 通常，微内核提供 **最小的进程管理、内存管理** 和 **通信设施**
- 通信通过消息传递在用户模块之间进行

- **优点**
  - 更容易扩展操作系统
  - 更容易将操作系统移植到新架构
  - 更可靠（内核模式下运行的代码更少）
  - 更安全
- **缺点**
  - 用户空间到内核空间通信的性能开销

## 模块

- 大多数现代操作系统实现内核模块
  - 采用面向对象的方法
  - 每个核心组件都是独立的
  - 每个组件通过已知接口相互通信
  - 每个组件可根据需要在内核中按需加载
- 总体而言，与分层类似，但更灵活

## Solaris 模块化方法

![](img/0f9477f9dd9e571abf0b2ce4550a9e88_116_0.png)

## 作业1

设计操作系统时采用的模块化内核方法和分层方法在哪些方面类似？
哪些方面不同？

## 虚拟机

- *虚拟机* 将分层方法推向了逻辑的极致。它将硬件和操作系统内核视为纯粹的硬件
- 虚拟机提供与底层裸硬件 *完全相同* 的接口
- 操作系统创建“*幻觉*”，即多个进程各自在自己的处理器上执行，并拥有自己的（虚拟）内存

![](img/0f9477f9dd9e571abf0b2ce4550a9e88_119_0.png)

- 物理计算机的资源被共享以创建虚拟机
- CPU 调度可以制造出用户拥有自己的处理器的假象
-  spooling 和文件系统可以提供虚拟卡片阅读器和虚拟行式打印机
- 普通用户分时终端充当虚拟机操作员的控制台

- **优点**
  - **提供系统资源的完全保护**
    - 每个虚拟机都与其他所有虚拟机隔离。这种隔离 however 不允许直接共享资源。
  - **能够共享同一硬件同时并发运行不同的操作系统**
  - **是操作系统研究和开发的完美载体**
    - 系统开发在虚拟机上进行，因此不会干扰正常系统操作。

### VMware 架构

| application | application | application | application |
|---|---|---|
|  | guest operating system (FreeBSD)<br>virtual CPU<br>virtual memory<br>virtual devices | guest operating system (Windows NT)<br>virtual CPU<br>virtual memory<br>virtual devices | guest operating system (Windows XP)<br>virtual CPU<br>virtual memory<br>virtual devices |
|  | virtualization layer | virtualization layer | virtualization layer |
|  | host operating system (Linux) | host operating system (Linux) | host operating system (Linux) |
|  | hardware<br>CPU<br>memory<br>I/O devices | hardware<br>CPU<br>memory<br>I/O devices | hardware<br>CPU<br>memory<br>I/O devices |

### Java 虚拟机

- 编译后的 Java 程序是平台中立的 **字节码**，由 Java 虚拟机（JVM）执行。

- JVM 由以下部分组成
  - class loader
  - class verifier
  - runtime interpreter

- **即时编译（JIT）** 编译器可提高性能

