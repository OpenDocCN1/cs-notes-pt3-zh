
## Analysis → Design

![](img/fcdc64f47992afbcce2e20fafbbb0375_225_0.png)

## 2 设计过程和设计质量

- 软件设计是一个迭代的过程，通过设计过程，需求被变换为用于构建软件的“蓝图”【体系结构设计/概要设计、接口设计】。
- 随着设计迭代的推进，后续的精化导致更低抽象层次的设计表示【构件级设计/详细设计、接口设计】。
- 正式的技术评审（technical review）和设计走查（walkthrough）可用于评估设计演化的质量。

## 3 Design Concepts

- **abstraction** — data, procedure
- **architecture** — the overall structure of the software
- **patterns** — “conveys the essence” of a proven design solution
- **modularity** — compartmentalization of data and function [数据和功能划分]
- **information hiding** — controlled interfaces
- **functional independence** — high cohesion and low coupling
- **refinement** — elaboration of detail for all abstractions
- **refactoring** — improve design without affecting behavior

### 3.1 Abstraction et al.

- Abstraction
  - process – extracting essential details
  - entity – a model or focused representation
- Information hiding
  - the suppression of inessential information
- Encapsulation
  - process – enclosing items in a container
  - entity – enclosure that holds the items

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

- “The overall structure of the software and the ways in which that structure provides conceptual integrity for a system.” [软件的整体结构和这种结构为系统提供概念上完整性的方式][SHA95a]
- 简而言之，体系结构是程序构件（模块）的结构或组织、这些构件交互的形式、以及构件所用的数据的结构。

### Architecture...

- **Structural properties.** This aspect of the architectural design representation defines the **components of a system (e.g., modules, objects, filters)** and **the manner** in which those components are packaged and interact with one another. For example, objects are packaged to encapsulate both data and the processing that manipulates the data and interact via the invocation of methods.
- **Extra-functional properties.** The architectural design description should address **how the design architecture achieves requirements for performance, capacity, reliability, security, adaptability, and other system characteristics.**
- **Families of related systems.** The architectural design should draw upon repeatable patterns that are commonly encountered in **the design of families of similar systems.** In essence, the design should have the ability to reuse architectural building blocks.

### 3.3 Patterns

- A pattern for software architecture describes a particular recurring design problem [某个再现的特定设计问题] that arises in specific design contexts, and presents a well-proven generic scheme for its solution. The solution scheme is specified by describing its constituent components, their responsibilities and relationships, and the ways in which they collaborate.

### Some Kinds of Patterns

- An **architectural pattern** expresses **a fundamental structural organization schema for software systems**. It provides a set of predefined subsystems, specifies their responsibilities, and includes rules and guidelines for organizing the relationships between them.
- A **design pattern** provides **a scheme for refining the subsystems** or components of a software system, or the relationships between them. It describes a commonly-recurring structure of communicating components that solves a general design problem within a particular context.
- An **idiom** is a low-level pattern **specific to a programming language**. An idiom describes how to implement particular aspects of components or the relationships between them using the features of the given language.
