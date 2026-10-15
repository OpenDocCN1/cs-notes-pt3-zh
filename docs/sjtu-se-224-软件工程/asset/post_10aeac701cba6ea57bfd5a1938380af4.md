
## 举例：Bridge模式

- 解释和毛笔刷的事情
  - 我们需要画出各种各样的毛笔刷制造画，画出各种山水、花鸟、人物等；
  - 我需要画笔
  - 不同粗细的笔（各种颜色可用笔不同长度、勾勒细节用笔粗细无法完成）
  - 不同颜色的笔（彩色画笔）
- 36只刷笔
  - 搭配笔杆、中、细等各种笔，一套12只，一共36只刷笔

![](img/bd1e40ee9d51e0bf88db831d8e65a09d_80_0.png)

- 解释毛笔刷的例子（续）
- 我需要画出各种毛笔刷在空中
- 3只毛笔、12种颜色，不同的毛笔使用不同的颜料

![](img/bd1e40ee9d51e0bf88db831d8e65a09d_80_1.png)

- 毛笔和颜料怎么分类？
  - 画笔的分类是按照笔的粗细
    - 而画笔的分类是按照笔的粗细
    - 笔的分类：3×12=36（将改变了加法）
    - 笔的分类：3+12=15
  - 采用
    - 12种颜色的毛笔刷可使用
- 解释为什么毛笔刷是可复用的原因是什么？
- 解释毛笔刷是可复用的原因是什么？
- 解释毛笔刷是可复用的原因是什么？
- 解释毛笔刷是可复用的原因是什么？

## Bridge模式

- 意图：
  - 将抽象与其实现解耦，使它们可以独立变化
- 图示：

![](img/bd1e40ee9d51e0bf88db831d8e65a09d_80_2.png)

## Design Pattern 的两本好书

- Erich Gamma, Richard Helm, Ralph Johnson, John Vlissides. "Design patterns: elements of reusable object-oriented software". Prentice Hall, 1994.
- Eric Freeman, Elisabeth Freeman, et al., "Head First Design Patterns", O'Reilly Media Inc., 2005.

![](img/bd1e40ee9d51e0bf88db831d8e65a09d_80_3.png)

## 框架(Framework)

框架是一个代码骨架，可以使用为解决问题的而设计的特定类或功能来填充这个代码骨架，使之丰满。

![](img/bd1e40ee9d51e0bf88db831d8e65a09d_80_4.png)

## 框架举例

- 1. MVC框架
  - J2EE
  - Struts
- 2. ORM 框架
  - EJB
  - Hibernate
- 3. 界面框架
  - Java界面框架: AWT, Swing, SWT, SwingWT, Java 2D, Java 3D.
  - JSF
  - AJAX界面框架: DWR, DOJO
- 4. 复合框架
  - Spring包含Web MVC, IOC, ...
  - Java EE 包含JSF, EJB, JAX-WS, IOC, ...

## Web MVC框架 (Java)举例

- JSP Model II
- J2EE
- Struts
- JSF
- Spring Web MVC
- WebWork
- TapeStry

## JSP Model II

![](img/bd1e40ee9d51e0bf88db831d8e65a09d_81_0.png)

## J2EE

![](img/bd1e40ee9d51e0bf88db831d8e65a09d_81_1.png)

## Struts 2

![](img/bd1e40ee9d51e0bf88db831d8e65a09d_81_2.png)

## SSH（Struts + Spring + Hibernate）

![](img/bd1e40ee9d51e0bf88db831d8e65a09d_81_3.png)

## Software Engineering

## 设计工程

- 软件架构设计
- 软件设计的原则
- 软件设计的复用
- 软件设计的质量

## 设计工程

## 软件设计的质量要求

- 1) 设计应当模块化、高内聚、低耦合。
  - 支持多人合作开发
  - 易于测试和修改
  - 能够以规范化实现
- 2) 设计应当包含数据、体系结构、接口和构件的清楚的表示。
- 3) 设计应根据软件需求采用可重复使用的方法进行。
- 4) 应该使用能够有效地传其意义的表示法来表达设计模型。

## 7种软件设计的坏味道

- 1) 僵化性（Rigidity）
  - 很难对软件进行改动，因为每个改动都会迫使对系统其他部分的许多改动
- 2) 脆弱性（Fragility）
  - 对系统的改动会导致系统中和改动的地方在概念上无关的许多地方出现问题
- 3) 牢固性（Immobility）
  - 很难解开系统某部分与其他部分之间的纠结，从而而使其中任何部分可以分离出来被其它系统复用

## 4) 粘滞性（Viscosity）

- 做正确的事比做错误的事困难。表现为两种形式：
  - 软件粘滞性
    需要对软件进行改动时，可能存在多种方法。有的方法可能很快但质量较差，有的慢、质量好。另一方面方法破坏了现有的设计质量。如果，破坏掉现有的设计质量比保持现有设计质量的修改要容易实施时，我们就称该软件具有“软件粘滞性”。
  - 环境粘滞性
    当开发环境迟钝、低效时，就会产生环境粘滞性。
    例如，如果编译时间很长，那么开发人员可能会放弃那些能够保持质量、但是需要导致大规模重新编译的改动。

- 5) 不必要的复杂性（Needless Complexity）
  - 设计中包含没有任何好处的基础结构。
- 6) 不必要的重复（Needless Repetition）
  - 设计中包含一些一再重复的结构，这些结构本来可以通过一个拷贝或继承来统一。
  - 使用Cut/Copy/Paste实现代码级的软件复用容易导致这一问题
  - 这种代码级别的冗余，将带来修改上的问题
- 7) 晦涩性（Opacity）
  - 很难以读和理解。不要相信你永远都会如此清楚地了解了你的程序、行为吗，“会冲突一切”。要始终在阅读者的角度进行设计

## Software Engineering

## 软件工程
Module: 构建设计模型

Shanghai Jiao Tong University

上海交通大学软件工作中心

## 构建设计模型

## 构建设计模型

- 设计工程中的重要环节
- 设计模型是平台有关模型
- 关注 How
- 两种建模的方法
  - 结构化设计
  - 面向对象设计
  - ……

@第3.2节和第7章.教材

## 分析模型 VS. 设计模型

| Analysis Model | Design Model |
|---|---|
| • Focus on understanding the problem | • Focus on understanding the solution |
| • Idealized design | • Operations and attributes |
| • Behavior | • Performance |
| • System structure | • Close to real code |
| • Functional requirements | • Object lifecycles |
| • A small model | • Nonfunctional requirements |
| | • A large model |

## 软件工程
Module: 结构化设计

## 结构化设计

- 结构化设计概述
- 结构化设计——概要设计
- 过程设计——详细设计

@3.2节·教材

## 结构化设计 (Structured Design, SD)

- 结构化设计是将结构化分析得到的数据流图映射成软件结构的一种设计方法
- 强调模块化、自顶向下逐步求精、信息隐蔽、高内聚低耦合等设计准则

## 结构化设计的内容

- 结构设计——概要设计
  - 结构图(Structure Chart)
  - 物理数据模型
- 过程设计——详细设计
  - 模块的处理过程
  - N-S图、PAD、PDL等

## 结构化设计

- 结构化设计概述
- 结构化设计——概要设计
- 过程设计——详细设计

## 结构化设计的工具——结构图

- 用结构图(Structure Chart)来描述软件系统的体系结构
- 描述一个软件系统由哪些模块组成，以及模块之间的调用关系
- 结构图的基本成分有：模块、调用和数据

![](img/bd1e40ee9d51e0bf88db831d8e65a09d_84_0.png)
