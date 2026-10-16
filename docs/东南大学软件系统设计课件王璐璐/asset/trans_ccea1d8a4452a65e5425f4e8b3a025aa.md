
## 开发视图...

- 开发视图的风格
  - 使用层次式风格，定义4或6层子系统。
  - 每层均有良好的职责、设计规则，即某层子系统依靠同层次的或更低层次的子系统，从而减少了具有复杂模块依赖关系的网路开发量，得到层次式的简单发布策略。
  - 各个层次，层次越低，通用性越强。以保证需求变更时，所做的改动最小。

## 开发视图。。。

## 空中交通管理（ATC）系统的分层开发视图

![](img/6b451d038dc64487adac52ab7c5c2495_118_0.png)

## 开发视图...

- 开发结构示例

图-6是图-3（b）（ P18 ）的开发视图。第1层和第2层组成了一个领域无关的分布式基础设施，贯穿于整个产品线中，并且与硬件平台、操作系统或数据库管理系统等无关。第3层增加了空中交通管制系统的框架，以形成一个领域特定的软件体系结构。第4层使用该框架建立一个功能平台，第5层则依赖于具体客户和产品，包含了大部分用户接口以及与外部系统的接口。

## 进程视图

- 进程视图（process view）也称为并发视图，侧重于系统的运行特性，主要关注一些非功能性的需求，例如系统的性能和可用性。
- 进程视图强调并发性、分布性、系统集成性和容错能力，以及从逻辑视图中的主要抽象如何适合进程结构—即在哪个控制流程上，对象的操作被真正地执行。

## 进程视图…

## 通信系统ACS的局部进程视图

进程蓝图示例

![](img/6b451d038dc64487adac52ab7c5c2495_122_0.png)

终端进程

控制器进程

主控制器任务

低速率控制器任务

高速率控制器任务

图5——Télic PABX的进程蓝图（部分）

## 进程视图

- （2）进程视图可以描述成多层抽象，每个级别分别关注不同的方面
- （3）多种风格适用于进程视图，如：
  - 管道-过滤器、客户端-服务器（多客户端/单服务器，单客户端/多服务器）。

## 物理视图

- 物理视图（physical view）主要考虑如何把软件映射到硬件上；
- 它通常要考虑到系统性能、规模、可靠性等；解决系统拓扑结构、系统安装、通信等问题。

## 物理视图

- 软件在计算机网络或处理节点上运行，被识别的各种元素（网络、过程、任务和对象），需要被映射至不同的节点；
- 我们希望使用不同的物理配置：
  - 一些用于开发和测试，另外一些则用于不同地点和不同客户的部署
- 因此软件至节点的映射需要高度的灵活性及对源代码产生最小的影响。

## 物理视图

- 物理视图的标记法

![](img/6b451d038dc64487adac52ab7c5c2495_126_0.png)

## 物理视图

- 物理视图示例

图-8显示了大型ACS的可能硬件配置

C,F,K是三个不同容量的计算机类型，支持三个不同的可执行文件

![](img/6b451d038dc64487adac52ab7c5c2495_127_0.png)

图8——PABX的物理蓝图

![](img/6b451d038dc64487adac52ab7c5c2495_128_0.png)

图9——带有进程分配的小型PABX物理架构

![](img/6b451d038dc64487adac52ab7c5c2495_129_0.png)

图10——显示进程分配的较大PABX物理蓝图

## 场景

- 场景（scenarios）可以看做那些重要系统活动的抽象，它使4个视图有机联系起来。
- 四种视图的元素通过少量的重要场景（如更具普遍性的use case）来无缝地协同工作。
- 它可以帮助架构师找到体系结构的构件和它们之间的作用关系。
- 从某种意义上讲，场景是最重要的需求抽象。

## 场景

- 场景是其它视图的冗余（因而“+1”），但它有两点作用：
  - （1）在SA设计过程中，作为一个驱动来发现SA元素；
  - （2）在SA设计结束时，从书面上作为对SA原型测试的起点。

## 场景

- 场景的设计用对象场景图和对象交互图来表示。
- 场景蓝图的标记法
  - 对组件而言，标记法同逻辑视图类似，但使用进程视图的连接符号来表达对象之间的交互。

![](img/6b451d038dc64487adac52ab7c5c2495_133_0.png)

图 11——本地呼叫选择阶段场景的雏形

- 1. Joe的电话控制器检测和校验摘机状态的变换，并发送消息唤醒相应的终端对象。
- 2. 终端分配一些资源，并要求控制器发出拨号音。
- 3. 控制器接受拨号并传递给终端。
- 4. 终端使用拨号方案来分析数字流。
- 5. 有效的数字序列被键入，终端开始会话。

## 二、“4+1”视图模型

- （4）并不是所有的软件架构都需要“4+1”视图。无用的视图可以从架构描述中省略。
  - 比如：只有一个处理器，则可以省略物理视图；而如果仅有一个进程或程序，则可以省略过程视图。对于非常小型的系统，甚至可能逻辑视图与开发视图非常相似，而不需要分开的描述。
  - 但一般情况下，场景对于所有的情况均适用。

## 三、软件体系结构的核心模型

- SA核心模型由五种元素构成
  - 组件（component），
  - 连接件（connector），
  - 配置（configuration），
  - 端口（port）
  - 角色（role）。

## 三、软件体系结构核心模型…

![](img/6b451d038dc64487adac52ab7c5c2495_137_0.png)

## 三、软件体系结构的核心模型

- 组件：具有某种功能的可重用的软件模块单元，表示了系统中主要的计算单元和数据存储。组件有两种：复合组件和原子组件。复合组件由其它复合组件和原子组件通过连接而成。
- 连接件：表示了组件之间的交互，简单的连接件有：管道（pipe）、过程调用（procedure-call）、事件广播（event broadcast）等。复杂的连接件有：客户-服务器（client-server）通信协议，数据库和应用之间SQL连接等。
- 配置：表示了组件和连接件的拓扑逻辑和约束。

```
Configuration GasStation
  Component Customer
    Port Pay = paylx → Pay
    Port Gas = take → pump?x → Gas
    Computation = Pay.pay?x → Gas.take → Gas.pump?x → Computation
  Component Cashier
    Port Customer1 = pay?x → Customer1
    Port Customer2 = pay?x → Customer2
    Port Topump = pump?x → Topump
    Computation = Customer1.pay?x → Topump.pump?x → Computation
      [] Customer2.pay?x → Topump.pump?x → Computation
  Component Pump
    Port Oil1 = take → pump?x → Oil1
    Port Oil2 = take → pump?x → Oil2
    Port Fromcashier = pump?x → Fromcashier
    Computation = Fromcashier.pump?x → Fromcashier
      (Oil1.take → Oil1.pump?x → Computation)
      [] (Oil2.take → Oil2.pump?x → Computation)
  Connector Customer_Cashier
    Role Givemoney = pay?x → Givemoney
    Role Getmoney = pay?x → Getmoney
    Glue = Givemoney.pay?x → Getmoney.pay?x → Glue
  Connector Customer_Pump
    Role Getoil = take → pump?x → Getoil
    Role Giveoil = take → pump?x → Giveoil
    Glue = Getoil.take → Giveoil.take → Giveoil.pump?x → Getoil.pump?x → Glue
  Connector Cashier_Pump
    Role Tell = pump?x → Tell
    Role Know = pump?x → Know
    Glue = Tell.pump?x → Know.pump?x → Glue
  Instances
    Customer1: Customer
    Customer2: Customer
    cashier: Cashier
    pump: Pump
    Customer1_cashier: Customer_Cashier
    Customer2_cashier: Customer_Cashier
    Customer1_pump: Customer_Pump
    Customer2_pump: Customer_Pump
    cashier_pump: Cashier_Pump
  Attachments
    Customer1.Pay as Customer1_cashier.Givemoney
    Customer1.Gas as Customer1_pump.Getoil
    Customer2.Pay as Customer2_cashier.Givemoney
    Customer2.Gas as Customer2_pump.Getoil
    cashier.Customer1 as Customer1_cashier.Getmoney
    cashier.Customer2 as Customer2_cashier.Getmoney
    cashier.Topump as cashier_pump.Tell
    pump.Fromcashier as cashier_pump.Know
    pump.Oil1 as Customer1_pump.Giveoil
    pump.Oil2 as Customer2_pump.Giveoil
End GasStation.
```

![](img/6b451d038dc64487adac52ab7c5c2495_140_0.png)

图3：加油站系统的架构。

![](img/6b451d038dc64487adac52ab7c5c2495_140_1.png)

图7：图6中切片的架构表示。
