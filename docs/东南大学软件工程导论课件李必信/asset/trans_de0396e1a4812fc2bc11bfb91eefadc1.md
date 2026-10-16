

## Analysis → Design

![](img/fcdc64f47992afbcce2e20fafbbb0375_225_0.png)

## 2 设计过程和设计质量

- 软件设计是一个迭代的过程，通过设计过程，需求被变换为用于构建软件的“蓝图”【体系结构设计/概要设计、接口设计】。
- 随着设计迭代的推进，后续的精化导致更低抽象层次的设计表示【构件级设计/详细设计、接口设计】。
- 正式的技术评审（technical review）和设计走查（walkthrough）可用于评估设计演化的质量。

## 3 Design Concepts

- **abstraction** — 数据，过程
- **architecture** — 软件的整体结构
- **patterns** — “传达”一种经过验证的设计解决方案的“精髓”
- **modularity** — 数据和功能的分区 [数据和功能划分]
- **information hiding** — 受控的接口
- **functional independence** — 高内聚和低耦合
- **refinement** — 对所有抽象进行细节的阐述
- **refactoring** — 在不影响行为的情况下改进设计

### 3.1 Abstraction et al.

- Abstraction
  - process – 提取本质细节的过程
  - entity – 模型或聚焦的表示
- Information hiding
  - 无关信息的抑制
- Encapsulation
  - process – 将项目封闭在容器中的过程
  - entity – 容纳项目的封闭物

### Data Abstraction

- 实数
- 对象
- 类
- 构件
- ……

数据抽象是描述数据对象的命名数据集合。

例如，“门”的数据抽象将包含一组描述门的属性：门的类型/转动方向/开门机构、重量和尺寸等

![](img/fcdc64f47992afbcce2e20fafbbb0375_229_0.png)

| door |
| --- |
| manufacturer |
| model number |
| type |
| swing direction |
| inserts |
| lights |
| &nbsp;&nbsp;type |
| &nbsp;&nbsp;number |
| weight |
| opening mechanism |

implemented as a data structure

### Procedural Abstraction

![](img/fcdc64f47992afbcce2e20fafbbb0375_230_0.png)

open

details of enter algorithm

implemented with a "knowledge" of the object that is associated with enter

过程抽象是指具有明确和有限功能的指令序列。

例如，“开”隐含了一长串的过程性步骤：走到门前、伸手并抓住把手、转动把手并拉门、推开打开的门等

### 3.2 Architecture

- “软件的整体结构和这种结构为系统提供概念上完整性的方式。” [软件的整体结构和这种结构为系统提供概念上完整性的方式][SHA95a]
- 简而言之，体系结构是程序构件（模块）的结构或组织、这些构件交互的形式、以及构件所用的数据的结构。

### Architecture...

- **Structural properties.** 体系结构设计表示的这一方面定义了**系统的组件（例如，模块、对象、过滤器）**以及**这些组件的打包方式**和**彼此交互的方式**。例如，对象被打包以封装数据和处理该数据的处理，并通过方法调用进行交互。
- **Extra-functional properties.** 体系结构设计描述应解决**设计体系结构如何实现性能、容量、可靠性、安全、适应性以及其他系统特性方面的需求**。
- **Families of related systems.** 体系结构设计应利用在**类似系统族的设计中**常见可重复的模式。实质上，设计应具有重用体系结构构建模块的能力。

### 3.3 Patterns

- 软件体系结构的模式描述了在特定设计上下文中出现的某个再现的特定设计问题 [某个再现的特定设计问题]，并提出了一种经过充分验证的通用方案来解决它。解决方案方案通过描述其构成组件、它们的职责和关系以及它们协作的方式来指定。

### Some Kinds of Patterns

- **architectural pattern** 表达了**软件系统的基本结构组织模式**。它提供了一组预定义的子系统，指定了它们的职责，并包括组织它们之间关系的规则和指导方针。
- **design pattern** 为**细化软件系统的子系统或组件，或它们之间的关系**提供了一种方案。它描述了在特定上下文中解决通用设计问题的通信组件的常见重复结构。
- **idiom** 是一种特定于编程语言的低级模式**。**idiom** 描述了如何使用给定语言的特性来实现组件的特定方面或它们之间的关系。

