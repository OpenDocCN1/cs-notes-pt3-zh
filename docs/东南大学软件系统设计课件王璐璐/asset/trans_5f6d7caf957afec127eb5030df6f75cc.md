

## 软件架构概述

lliao@seu.edu.cn

## 第Ⅰ章:概论

- （一）软件危机
- （二）软件架构的兴起和发展
- （三）软件重用
- （三）面向对象与重用
- （四）构件与重用

## 一、软件危机

- 第一次软件危机（1945 to 1968）
  - 危机表现
- 软件生产效率低下,软件成本高: 软件开发成本和进度的估计常常很不准确。
- 软件产品质量差: 用户对“已完成的”软件系统不满意的现象经常发生。
- 软件产品难以(不能)维护: 软件通常没有适当的文档资料

## 一、软件危机

- 第一次软件危机（1945 to 1968）
  - 危机根源
    - 人员知识结构单一
    - 手工作坊：code and fix
    - 理论体系不成熟软件开发：语言、工具、过程、方法、质量保证……
    - 软件开发管理不完善：规划、预算、可行性分析、风险预测与控制

## 一、软件危机

- 第二次软件危机（**1968 to 2001**）
  - 危机根源
    - 假设需求可以在开发前完全被理解
    - 与客户的交互仅发生在开始时（需求）和结束时（交付后）
    - 不幸的是该假设几乎从未成立

## 一、软件危机

- 第三次软件危机（2001年至今）
  - 危机表现
    - 变更/演化/重用（质量、效率、成本）
    - 知识产权问题、安全问题
  - 危机根源
    - 大量遗产系统的挖掘和重用
    - 大量开源软件/代码的使用
    - 普遍存在的动态/不确定需求

## 软件危机数据——项目拖延或取消的事例

![](img/6b451d038dc64487adac52ab7c5c2495_25_0.png)

| 项目结果 | 1994 | 1996 | 1998 | 2000 | 2002 | 2004 |
|---|---:|---:|---:|---:|---:|---:|
| 成功（Succeeded） | 16% | 27% | 26% | 28% | 34% | 29% |
| 失败（Failed） | 31% | 40% | 28% | 23% | 15% | 18% |
| 受挑战（Challenged） | 53% | 33% | 46% | 49% | 51% | 53% |

## 软件危机数据

## MODERN RESOLUTION FOR ALL PROJECTS

| | 2011 | 2012 | 2013 | 2014 | 2015 |
|---|---|---|---|---|---|
| SUCCESSFUL | 29% | 27% | 31% | 28% | 29% |
| CHALLENGED | 49% | 56% | 50% | 55% | 52% |
| FAILED | 22% | 17% | 19% | 17% | 19% |

The Modern Resolution (OnTime, OnBudget, with a satisfactory result) of all software projects from FY2011-2015 within the new CHAOS database. Please note that for the rest of this report CHAOS Resolution will refer to the Modern Resolution definition not the Traditional Resolution definition.

现代解决方案（按时、按预算、取得令人满意的结果）是 FY2011-2015 年间新 CHAOS 数据库中所有软件项目的现代解决方案。请注意，在本报告的其余部分，CHAOS 解决方案将指现代解决方案定义，而非传统解决方案定义。

## CHAOS RESOLUTION BY PROJECT SIZE

|  | SUCCESSFUL | CHALLENGED | FAILED |
|---|---|---|---|
| Grand | 2% | 7% | 17% |
| Large | 6% | 17% | 24% |
| Medium | 9% | 26% | 31% |
| Moderate | 21% | 32% | 17% |
| Small | 62% | 16% | 11% |
| TOTAL | 100% | 100% | 100% |

The resolution of all software projects by size from FY2011-2015 within the new CHAOS database.

FY2011-2015 年间新 CHAOS 数据库中按规模划分的所有软件项目的解决方案。

## 二、软件架构的兴起和发展

- 1. 背景分析
- 2. 软件架构定义 - 百家之言
- 3. 软件架构的意义
- 4. 软件架构发展史

## 二、软件架构的兴起和发展

- I.背景分析
  - 小规模软件开发：算法 + 数据结构 is enough!
  - 大规模软件开发：总体的系统设计和规格说明 must be more important!
    ⇒软件架构（Software architecture）

## 二、软件架构的兴起和发展

### ❀ 2.软件架构定义 – 百家之言

（1）Dewayne Perry和Alex Wolf的定义（1992）

软件架构是具有某种特定形式的结构化元素（即构件）的集合，包括处理构件、数据构件和连接构件。处理构件负责对数据进行加工，数据构件是被加工的信息，连接构件把架构的不同部分组合连接起来。

> (A set of architectural (or, if you will, design) elements that have a particular form. Perry and Wolf distinguish between processing elements, data elements, and connecting elements.)

> （一组具有特定形式的结构化元素（或，如果你愿意，设计元素）。Perry 和 Wolf 将其区分为处理元素、数据元素和连接元素。）

## 二、软件架构的兴起和发展

2. 软件架构定义 - 百家之言

（2）Mary Shaw 和 David Garlan 的定义（1993）

软件架构是软件设计过程中的一个层次，这一层次超越计算过程中的算法设计和数据结构设计。架构问题包括总体组织和全局控制、通信协议、同步、数据存取，给设计元素分配特定功能，设计元素的组织、规模和性能，在各设计方案间进行选择等。软件架构处理算法与数据结构关于整体系统结构设计和描述方面的一些问题，如全局组织和全局控制结构，关于通信、同步与数据存取的协议，设计构件功能定义，物理分布与合成，设计方案的选择、评估与实现等。

## 二、软件架构的兴起和发展

- 2. 软件架构定义 - 百家之言

（3）Hayes Roth的定义（1994）

软件架构是一个抽象的系统规约，主要包括用其行为来描述的功能构件和构件之间的相互连接、接口和关系。

> （...an abstract system specification consisting primarily of functional components described in terms of their behaviors and interfaces and component-component interconnections.）

> （...主要由以其行为和接口描述的功能构件以及构件与构件之间的互连构成的抽象系统规范。）

## 二、软件架构的兴起和发展

- 2. 软件架构定义 - 百家之言

（4）Booch, Rumbaugh, and Jacobson (1999)

> An architecture is the set of **significant decisions** about the organization of a software system, **the selection** of the structural elements and their interfaces by which the system is composed, **together with their behavior** as specified in the collaborations among those elements, **the composition** of these structural and behavioral elements into progressively larger subsystems, and the architectural style that guides this organization---these elements and their interfaces, their collaborations, and their composition (The UML Modeling Language User Guide, Addison-Wesley, 1999).

> 一个架构是关于软件系统组织的**重要决策**的集合，**选择**构成系统的结构元素及其接口，**连同其行为**，如这些元素之间协作中所指定的，**这些结构和行为元素的组合**形成越来越大的子系统，以及指导此组织的架构风格——这些元素及其接口、它们的协作以及它们的组合（《UML 建模语言用户指南》，Addison-Wesley，1999）。

