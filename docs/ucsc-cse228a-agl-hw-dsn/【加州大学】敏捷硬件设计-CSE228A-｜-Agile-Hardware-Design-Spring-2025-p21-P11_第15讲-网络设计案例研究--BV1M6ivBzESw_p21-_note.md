# 敏捷硬件设计：CSE228A：第15讲 - 网络设计案例研究 🧠

在本节课中，我们将通过一个网络设计的案例研究，学习如何运用继承、参数化等特性来构建一个可复用的网络组件库。我们将从最简单的交叉开关（Crossbar）开始，逐步扩展到环形网络（Ring），并最终构建一个参数化的网络生成器库。

![](img/326f273cc805b3fbb7a6a01b08c659c2_1.png)

## 概述

![](img/326f273cc805b3fbb7a6a01b08c659c2_3.png)

我们将遵循渐进式设计流程：从一个简单的、可工作的设计开始，然后逐步扩展其功能。在这个过程中，我们将重点关注如何利用继承来共享代码、提高生产力，并最终构建一个灵活的网络库。

---

## 从交叉开关开始

![](img/326f273cc805b3fbb7a6a01b08c659c2_5.png)

上一节我们介绍了设计流程，本节中我们来看看如何构建一个基础的网络组件——交叉开关。

交叉开关是一种简单的网络组件，它拥有固定数量的输入端口和输出端口，可以实现任意输入到任意输出的连接。其核心挑战在于，当多个输入试图同时写入同一个输出端口时，需要进行仲裁。

![](img/326f273cc805b3fbb7a6a01b08c659c2_7.png)

### 定义消息类型

![](img/326f273cc805b3fbb7a6a01b08c659c2_9.png)

![](img/326f273cc805b3fbb7a6a01b08c659c2_11.png)

首先，我们需要定义在网络中传输的消息类型。消息不仅包含有效载荷，还需要包含目的地址。

![](img/326f273cc805b3fbb7a6a01b08c659c2_13.png)

```scala
class Message[T <: Data](val addrWidth: Int, val dataType: T) extends Bundle {
  val addr = UInt(addrWidth.W)
  val data = dataType.cloneType
}
```

### 交叉开关的IO端口

交叉开关的IO端口需要指定输入数量、输出数量和有效载荷大小。

![](img/326f273cc805b3fbb7a6a01b08c659c2_15.png)

```scala
class CrossbarIO[T <: Data](nIn: Int, nOut: Int, dataType: T) extends Bundle {
  val in = Flipped(Vec(nIn, Decoupled(new Message(log2Ceil(nOut), dataType))))
  val out = Vec(nOut, Decoupled(dataType.cloneType))
}
```

![](img/326f273cc805b3fbb7a6a01b08c659c2_17.png)

### 交叉开关的实现

![](img/326f273cc805b3fbb7a6a01b08c659c2_19.png)

![](img/326f273cc805b3fbb7a6a01b08c659c2_21.png)

![](img/326f273cc805b3fbb7a6a01b08c659c2_23.png)

以下是交叉开关的核心实现代码。我们为每个输出端口实例化一个仲裁器，并使用函数式编程和循环来简洁地连接所有逻辑。

![](img/326f273cc805b3fbb7a6a01b08c659c2_25.png)

![](img/326f273cc805b3fbb7a6a01b08c659c2_27.png)

```scala
class Crossbar[T <: Data](nIn: Int, nOut: Int, dataType: T) extends Module {
  val io = IO(new CrossbarIO(nIn, nOut, dataType))
  // 为每个输出实例化一个仲裁器
  val arbiters = Seq.fill(nOut)(Module(new RRArbiter(new Message(log2Ceil(nOut), dataType), nIn)))
  // 连接输入就绪信号
  for (i <- 0 until nIn) {
    io.in(i).ready := arbiters.map(_.io.in(i).ready).reduce(_ && _)
  }
  // 连接仲裁器输入和输出
  for ((arb, outPort) <- arbiters.zip(io.out)) {
    arb.io.in <> io.in.map(_.bits)
    outPort <> arb.io.out
  }
}
```

![](img/326f273cc805b3fbb7a6a01b08c659c2_29.png)

通过这种方式，我们可以轻松实例化一个交叉开关：`val myCrossbar = Module(new Crossbar(4, 4, UInt(64.W)))`。

---

## 使用Case Class优化参数管理

为了使设计更易于管理，我们可以使用Scala的Case Class来封装参数。

### 定义参数Case Class

![](img/326f273cc805b3fbb7a6a01b08c659c2_31.png)

![](img/326f273cc805b3fbb7a6a01b08c659c2_33.png)

![](img/326f273cc805b3fbb7a6a01b08c659c2_35.png)

```scala
case class CrossbarParams(nHosts: Int, payloadWidth: Int)
```

![](img/326f273cc805b3fbb7a6a01b08c659c2_37.png)

### 修改模块以使用参数

![](img/326f273cc805b3fbb7a6a01b08c659c2_39.png)

然后，我们修改交叉开关模块，使其接收一个参数对象，而不是多个独立参数。

```scala
class Crossbar(params: CrossbarParams) extends Module {
  val io = IO(new CrossbarIO(params.nHosts, params.nHosts, UInt(params.payloadWidth.W)))
  // ... 内部实现逻辑与之前类似，但使用params.nHosts等字段
}
```

实例化时只需传入参数对象：`val myCrossbar = Module(new Crossbar(CrossbarParams(4, 64)))`。这使代码更简洁，尤其在参数变得复杂时更具可扩展性。

---

![](img/326f273cc805b3fbb7a6a01b08c659c2_41.png)

## 引入类型参数化

为了进一步提高灵活性，我们可以为有效载荷引入类型参数。

### 参数化消息和端口

```scala
case class CrossbarParams[T <: Data](nHosts: Int, payloadType: T)
class Crossbar[T <: Data](params: CrossbarParams[T]) extends Module {
  val io = IO(new CrossbarIO(params.nHosts, params.nHosts, params.payloadType))
  // ... 实现逻辑
}
```

现在，交叉开关可以支持任意数据类型的有效载荷，例如`UInt`、`SInt`或自定义的Bundle。

![](img/326f273cc805b3fbb7a6a01b08c659c2_43.png)

---

![](img/326f273cc805b3fbb7a6a01b08c659c2_45.png)

## 从单跳网络到多跳网络

![](img/326f273cc805b3fbb7a6a01b08c659c2_47.png)

随着端点数量的增加，单跳的交叉开关在可扩展性上会遇到瓶颈（布线复杂、逻辑集中）。因此，我们需要转向多跳网络拓扑，例如环形网络。

### 环形网络简介

![](img/326f273cc805b3fbb7a6a01b08c659c2_49.png)

在环形网络中，每个路由器连接其邻居，并有一个端口连接主机。消息沿着环传递：如果目的地是当前节点，则消息被取出；否则，继续向前传递。这是一种简单的起点。

![](img/326f273cc805b3fbb7a6a01b08c659c2_51.png)

![](img/326f273cc805b3fbb7a6a01b08c659c2_53.png)

![](img/326f273cc805b3fbb7a6a01b08c659c2_55.png)

### 环形路由器实现草图

环形路由器的核心逻辑是判断消息目的地并决定转发方向。

![](img/326f273cc805b3fbb7a6a01b08c659c2_57.png)

```scala
class RingRouter[T <: Data](params: NetworkParams[T], myId: Int) extends Module {
  val io = IO(new RouterIO(3, params.payloadType)) // 3个端口：左、右、主机
  // 判断消息是否发往本机
  val isForMe = io.in.bits.addr === myId.U
  // 输出选择逻辑：发往主机或转发
  when (isForMe) {
    io.hostOut <> io.in
    io.networkOut.valid := false.B
  } .otherwise {
    io.hostOut.valid := false.B
    io.networkOut <> io.in
  }
}
```

### 连接成环

![](img/326f273cc805b3fbb7a6a01b08c659c2_59.png)

使用函数式编程的`foldLeft`可以优雅地将多个路由器连接成一个环。

![](img/326f273cc805b3fbb7a6a01b08c659c2_61.png)

```scala
class RingNetwork[T <: Data](params: NetworkParams[T]) extends Module {
  val routers = Seq.tabulate(params.nHosts)(id => Module(new RingRouter(params, id)))
  // 使用foldLeft连接相邻路由器
  routers.zipWithIndex.foldLeft(routers.last) { case (prev, (curr, idx)) =>
    curr.io.left <> prev.io.right
    curr
  }
  // 连接主机端口
  routers.zip(io.ports).foreach { case (r, p) => p <> r.io.host }
}
```

---

## 利用继承构建网络库

现在，我们有了交叉开关和环形网络。它们都是网络，可以共享很多代码。我们可以创建一个抽象的网络基类。

![](img/326f273cc805b3fbb7a6a01b08c659c2_63.png)

### 定义抽象网络类

首先，定义通用的网络参数和IO端口。

![](img/326f273cc805b3fbb7a6a01b08c659c2_65.png)

![](img/326f273cc805b3fbb7a6a01b08c659c2_67.png)

![](img/326f273cc805b3fbb7a6a01b08c659c2_69.png)

```scala
case class NetworkParams[T <: Data](nHosts: Int, payloadType: T)
abstract class Network[T <: Data](params: NetworkParams[T]) extends Module {
  val io = IO(Vec(params.nHosts, new BidirectionalPort(params.payloadType)))
}
```

![](img/326f273cc805b3fbb7a6a01b08c659c2_71.png)

![](img/326f273cc805b3fbb7a6a01b08c659c2_73.png)

### 让具体网络继承基类

![](img/326f273cc805b3fbb7a6a01b08c659c2_75.png)

![](img/326f273cc805b3fbb7a6a01b08c659c2_77.png)

然后，让交叉开关和环形网络都继承这个抽象类。这样，它们就自动拥有了定义好的IO端口。

```scala
class Crossbar(params: CrossbarParams[T]) extends Network(params) {
  // 无需再声明io，直接使用继承来的io
  // ... 交叉开关的具体实现
}
class RingNetwork(params: NetworkParams[T]) extends Network(params) {
  // ... 环形网络的具体实现
}
```

![](img/326f273cc805b3fbb7a6a01b08c659c2_79.png)

![](img/326f273cc805b3fbb7a6a01b08c659c2_81.png)

这减少了重复代码，并建立了一个统一的设计模式。

---

![](img/326f273cc805b3fbb7a6a01b08c659c2_83.png)

## 构建更通用的路由器与网络

为了支持更复杂的拓扑（如双向环、网格、环面），我们需要进一步抽象。

![](img/326f273cc805b3fbb7a6a01b08c659c2_85.png)

![](img/326f273cc805b3fbb7a6a01b08c659c2_87.png)

### 通用路由器抽象

一个通用路由器包含一个内部交叉开关和路由逻辑函数。

![](img/326f273cc805b3fbb7a6a01b08c659c2_89.png)

```scala
abstract class Router[T <: Data](params: NetworkParams[T], numPorts: Int) extends Module {
  val io = IO(new RouterIO(numPorts, params.payloadType))
  val crossbar = Module(new Crossbar(CrossbarParams(numPorts, params.payloadType)))
  // 路由逻辑：根据目的地址决定下一跳端口
  def routeLogic(addr: UInt): UInt
  // 连接输入到交叉开关，并使用routeLogic决定输出端口
}
```

### 多跳网络抽象

一个多跳网络由多个路由器按照特定拓扑连接而成。

![](img/326f273cc805b3fbb7a6a01b08c659c2_91.png)

![](img/326f273cc805b3fbb7a6a01b08c659c2_93.png)

```scala
abstract class MultiHopNetwork[T <: Data, R <: Router[T]](params: NetworkParams[T]) extends Network(params) {
  val routers: Seq[R]
  def connectRouters(routers: Seq[R]): Unit // 抽象方法，由子类定义具体连接方式
  // 连接路由器到外部端口
  routers.zip(io.ports).foreach { case (r, p) => p <> r.io.hostPort }
}
```

![](img/326f273cc805b3fbb7a6a01b08c659c2_95.png)

![](img/326f273cc805b3fbb7a6a01b08c659c2_97.png)

### 实现双向环

![](img/326f273cc805b3fbb7a6a01b08c659c2_99.png)

利用上述抽象，实现双向环变得非常简洁。我们只需提供具体的路由逻辑和连接方式。

```scala
class BidirectionalRingRouter[T <: Data](params: NetworkParams[T], myId: Int) extends Router(params, 3) {
  override def routeLogic(addr: UInt): UInt = {
    val dist = Mux(addr > myId.U, addr - myId.U, myId.U - addr)
    val distWrap = params.nHosts.U - dist
    Mux(dist < distWrap, 1.U, 2.U) // 选择更近的方向
  }
}
class BidirectionalRingNetwork[T <: Data](params: NetworkParams[T]) extends MultiHopNetwork[T, BidirectionalRingRouter[T]](params) {
  override val routers = Seq.tabulate(params.nHosts)(id => Module(new BidirectionalRingRouter(params, id)))
  override def connectRouters(routers: Seq[BidirectionalRingRouter[T]]): Unit = {
    // 使用foldLeft连接成环
  }
}
```

![](img/326f273cc805b3fbb7a6a01b08c659c2_101.png)

![](img/326f273cc805b3fbb7a6a01b08c659c2_103.png)

### 实现2D环面网络

同样，我们可以用类似的模式实现更复杂的2D环面网络，只需定义其特定的路由逻辑（考虑行和列）和2D连接方式即可。大部分基础功能都已由抽象类提供。

![](img/326f273cc805b3fbb7a6a01b08c659c2_105.png)

![](img/326f273cc805b3fbb7a6a01b08c659c2_107.png)

---

## 工厂模式与模式匹配

最后，我们可以创建一个工厂对象，根据传入的参数类型，动态生成对应的网络实例。这为库的使用者提供了极大的便利。

![](img/326f273cc805b3fbb7a6a01b08c659c2_109.png)

![](img/326f273cc805b3fbb7a6a01b08c659c2_110.png)

```scala
object Network {
  def apply[T <: Data](params: NetworkParams[T]): Network[T] = params match {
    case p: CrossbarParams[T] => new Crossbar(p)
    case p: RingParams[T] => new RingNetwork(p)
    case p: TorusParams[T] if p.dim == 1 => new RingNetwork(p.toRingParams) // 模式匹配优化
    case p: TorusParams[T] => new TorusNetwork(p)
    case _ => throw new IllegalArgumentException("Unknown network parameters")
  }
}
// 用户使用方式
val myNet = Network(TorusParams(dim=2, nHosts=16, payloadType=UInt(32.W)))
```

---

## 总结与设计经验

本节课中我们一起学习了如何通过渐进式设计构建一个参数化的网络生成器库。

**核心设计经验总结：**
1.  **快速启动**：从一个小型、可运行的设计开始，确保其功能正确。
2.  **渐进扩展**：逐步添加功能和优化，每次迭代都保持一个可工作的状态。
3.  **识别抽象**：当编写多个相似模块或发现复制粘贴的代码时，就是提取通用抽象的好时机。
4.  **利用语言特性**：充分利用Scala和Chisel的特性，如Case Class、类型参数、继承、函数式编程和模式匹配，来构建灵活、可复用的设计。
5.  **构建库**：通过抽象基类和工厂模式，将相关组件组织成易于使用的库，提高未来项目的开发效率。

![](img/326f273cc805b3fbb7a6a01b08c659c2_112.png)

通过这个案例，我们展示了如何将敏捷开发思想应用于硬件设计，通过迭代和重构，最终得到一个强大而优雅的解决方案。