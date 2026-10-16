

## 浏览器/服务器风格

## 缺点

- B/S体系结构缺乏对动态页面的支持能力，没有集成有效的数据库处理功能。
- B/S体系结构系统扩展能力差，安全性难以控制。
- 采用B/S体系结构的应用系统，在数据查询等响应速度上，要远远地低于C/S体系结构。
- B/S体系结构的数据提交一般以页面为单位，数据的动态交互性不强，不利于在线事务处理 (OLTP) 应用。

## C/S+B/C内外有别模式

- 为了克服C/S与B/S各自的缺点，发挥各自的优点，在实际应用中，通常将二者结合起来；
- 遵循“内外有别”的原则：
  - 企业内部用户通过局域网直接访问数据库服务器
    - C/S结构；
    - 交互性增强；
    - 数据查询与修改的响应速度高；
  - 企业外部用户通过Internet访问Web服务器/应用服务器
    - B/S结构；
    - 用户不直接访问数据，数据安全；

![](img/da691714eec1b93795825838a75ee408_101_0.png)

## C/S+B/C查改有别模式

■ 选择“查改有别”的原则：

- 不管用户处于企业内外什么位置（局域网或Internet），凡是需要对数据进行更新操作的（Add、Delete、Update），都需要使用C/S结构；
- 如果只是执行一般的查询与浏览操作（Read/Query），则使用B/S结构。

![](img/da691714eec1b93795825838a75ee408_102_0.png)

## J2EE B/S+C/S Architecture

C/S与B/S的混合相当于分层风格里的“松耦合分层模式”

![](img/da691714eec1b93795825838a75ee408_102_1.png)

## 基于集群(Cluster)的C/S和B/S物理分布

- 事实上，功能层并不一定只驻留在同一台服务器上，数据层也是如此；
- 如果功能层(或数据层)分布在多台服务器上，那么就形成了基于集群(Cluster)的C/S物理分布模型。

![](img/da691714eec1b93795825838a75ee408_103_0.png)

## 集群(Cluster)

- A cluster is a group of loosely coupled servers that work together closely so that in many respects it can be viewed as though it were a single server.（一组松散耦合的服务器，共同协作，可被看作是一台服务器）
- Clusters are usually deployed to improve speed, reliability and availability over that provided by a single server, while typically being much more cost-effective than single computers of comparable speed or reliability.（用来改善速度、提高可靠性与可用性，降低成本）
- Load-balancing is a key issue in clusters.（负载平衡是集群里的一个关键要素）
- Physical cluster and logical cluster（物理集群、逻辑集群）

## 集群(Cluster)

![](img/da691714eec1b93795825838a75ee408_104_0.png)

## 集群的方法

- 集群内各服务器上的内容保持一致(通过冗余提高可靠性和可用性)

![](img/da691714eec1b93795825838a75ee408_104_1.png)

- 集群内各服务器上的内容之和构成系统完整的功能/数据，是对系统功能集合/数据集合的一个划分(通过分布式提高速度与并发性)

![](img/da691714eec1b93795825838a75ee408_104_2.png)

## A small catalog of architecture styles

| 体系结构风格 | 进一步细分 |
| --- | --- |
| 数据流系统 (Data flow) | 顺序批处理 (Batch Sequential) |
|  | 管道和过滤器 (Pipes and Filters) |
| 调用-返回系统 (call and return) | 主程序和子程序 (Main program and subroutine) |
|  | OO 系统 |
|  | 分层结构 (Layered) |
| 独立组件 (Independent components) | 通信过程 (Communicating Process) |
|  | 事件系统 | Implicit Invocation |
|  |  | Explicit Invocation |
| 虚拟机 (Virtual machine) | 解释器 (Interpreter) |
|  | 基于规则的系统 (Rule-Based System) |
| 数据为中心系统 (Data-centered) | 数据仓库 (Repository) |
|  | 超文本系统 ( Hypertext) |
|  | 黑板 ( Blackboard) |

## 独立构件风格

- Independent Components
  - Communicating Processes
  - Event Systems
    - Implicit Invocation
    - Explicit Invocation

|  | 完整性 | 组合性 | 抽象性 | 重用性 | 构建性 | 异构性 | 可分析性 |
| --- | --- | --- | --- | --- | --- | --- | --- |
| 独立构件 |  |  | + | + | + |  |  |

## 显式调用 vs. 隐式调用

- 显式调用：
  - 各个构件之间的互动是由显性调用函数或程序完成的。
  - 调用过程与次序是固定的，预先设定的。

- 隐式调用：
  - 调用过程与次序是不固定的，预先未知；
  - 各构件之间通过事件的方式进行交互。

![](img/da691714eec1b93795825838a75ee408_106_0.png)

## 事件系统的基本构成

![](img/da691714eec1b93795825838a75ee408_106_1.png)

| 功能 | 描述 |
|---|---|
| 分离的交互 | 事件发布者并不会意识到事件订阅者的存在。 |
| 多对象通信 | 采用发布/订阅消息传递，一个特定事件可以影响多个订阅者。 |
| 基于事件的触发器 | 控制流由接收者确定（基于发布的事件）。 |
| 异步 | 通过事件消息传递支持异步操作。 |

## 基于事件的隐式调用风格

## 基于事件的隐式调用风格

- 基本结构

![](img/da691714eec1b93795825838a75ee408_107_0.png)

- 特点：此类系统中，构件不直接调用一个过程，而是声明或广播一个或多个事件。系统中的其他构件可以将一过程注册为与它所关心的事件相关联。当某一个事件发生时，系统会调用所有与之关联的过程，即一个事件的激发隐含地导致了对其他模块的过程的调用。

- 构件：是这样的模块，其接口不仅提供一个过程的集合，还提供一个事件的集合。构件可以声明或广播一个或多个事件，或者向系统注册，来表明它希望相应的事件

- 连接件：有两类 — 对事件的显示或隐式调用。

- 适用于涉及低耦合构件集合的应用程序，尤其是必须动态重配置的应用程序。

- 优点：
  - 事件广播者不必知道哪些部件会被事件影响，部件之间关系弱。
  - 隐式调用有利于软件重用，因为允许任何构件注册相关事件；
  - 修改构件的接口并不影响别的构件，因而系统的演化、升级变得简单

- 缺点：
  - 构件不再拥有计算的控制权，一旦触发一个事件，它不能确定响应 的构件，也无法知道相关过程执行的顺序；在共享数据存储库的系 统中，资源管理器的性能和准确度成为十分关键的因素。
  - 数据交换问题。
  - 被调用的过程的语义依赖于被触发的事件的上下文约束，很难对系 统的正确性进行推理。

- 典型实例：
  - 最早出现在于守护进程、约束满足性检查和包交换网络等方面
  - 常用于：开发环境中集成各种工具、在用户界面中分离数据和表示
  - 典型实例：Windows的消息机制

## A small catalog of architecture styles

| 体系结构风格 | 进一步细分 |
| --- | --- |
| 数据流系统 (Data flow) | 顺序批处理 (Batch Sequential) |
|  | 管道和过滤器 (Pipes and Filters) |
| 调用-返回系统 (call and return) | 主程序和子程序 (Main program and subroutine) |
|  | OO 系统 |
|  | 分层结构 (Layered) |
| 独立组件 (Independent components) | 通信进程 (Communicating Process) |
|  | 事件系统 | Implicit Invocation |
|  |  | Explicit Invocation |
| 虚拟机 (Virtual machine) | 解释器 (Interpreter) |
|  | 基于规则的系统 (Rule-Based System) |
| 数据为中心系统 (Data-centered) | 数据仓库 (Repository) |
|  | 超文本系统 ( Hypertext) |
|  | 黑板 ( Blackboard) |

## 数据中心风格—仓库风格

![](img/da691714eec1b93795825838a75ee408_108_0.png)

The data-centered style.

- 目标：获得数据的易集成性
- 仓库 (Repositories) 风格的体系结构含两类构件:
  - 一个中央数据结构，表示当前状态
  - 一个独立构件的集合，对中央数据结构进行操作

