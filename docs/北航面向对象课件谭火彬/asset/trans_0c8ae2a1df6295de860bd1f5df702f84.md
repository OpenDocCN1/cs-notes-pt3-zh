

## UML是基于MOF四层模型

- 元元模型层(M3)
  - 包含了定义建模语言所需的元素(UML基础结构)
  - MetaClass, MetaAttribute, MetaOperation
- 元模型层(M2)
  - 定义了一种建模语言的结构和语法(UML上层结构)
  - 如UML: Class, Attribute, Operation
- 模型层(M1)
  - 定义了一个具体的系统的模型
  - 如采用UML表示的某系统模型
- 运行时(M0)
  - 包含了一个模型的对象在运行时的状态等
  - 如某系统运行时的对象和数据模型

## 四层元模型结构实例

M3(MOF)

M2(UML)

M1(User Model)

M0(Run-time instances)

![](img/32b9da3a6e0f048e7dd2e9664c939f9e_94_0.png)

## UML基础结构和上层结构

![](img/32b9da3a6e0f048e7dd2e9664c939f9e_95_0.png)

## UML基础结构中的Core包

![](img/32b9da3a6e0f048e7dd2e9664c939f9e_96_0.png)

### 内容安排

- 可视化建模
- UML
- UML组成结构
- UML概念模型
- 应用UML2建模

## UML2概念模型

UML上层结构
Superstructure

构造块
building blocks

通用机制
common mechanisms

构架
architecture

基本UML建模元素、关系和图

达到特定目标的通用UML方法

系统架构的UML视图

## 构造块

- 构造块(building blocks)
- 事物(things)
  - 结构、行为、分组、注释
- 关系(relationships)
  - 依赖、关联、泛化、实现
- 图(diagram)
  - 静态(7种): 类图、对象图、构件图、部署图、包图、组合结构图、外廓图
  - 动态(7种): 顺序图、通信图、时间图、交互纵览图、活动图、状态机图、用例图

## 事物(things)

- 结构(structural)事物
  - 类、接口
  - 用例、协作
  - 构件、工件、节点
- 行为(behavioral)事物
  - 交互、状态机、活动
- 分组(grouping)事物
  - 包、框架、模型、子系统...
- 注释(annotational)事物

## 关系

关系 relationships

- 依赖 dependency
- 关联 association
- 泛化 generalization
- 实现 realization

## 通用机制

- 规格说明(Specifications)
  - 文本维度的模型描述
- 修饰(Adornments)
  - 描述建模元素的细节信息
- 通用划分(Common Divisions)
  - 建模时对事物的划分方法
- 扩展机制(Extensibility Mechanisms)
  - 构造型、约束、标记值

## 规格说明(Specifications)

- UML模型至少具有两种维度：
  - 图形维度：使用图和图标可视化模型
  - 文本维度：各种建模元素的规格说明
- 规格说明
  - 模型元素的特征和语义的文本描述
  - 形成了承载模型的语义背板（semantic backplane），赋予模型意义，各种图仅仅是该背板的视图或者可视化投影
  - death by diagram(由于图形而死亡)

## 修饰(adornments)

UML表示法中的每一个元素都有一个基本符号，可以把各种修饰细节添加到这些符号上

只有在修饰增强了图的整体清晰性和可读性或者突出模型的某些重要特征时，才应该表示那些修饰

![](img/32b9da3a6e0f048e7dd2e9664c939f9e_104_0.png)

## 通用划分(续)

- 类型和角色的分离(UML2新增)

  任何作为其它实体结构的一部分实体(如属性)都具有两个方面的特性：

  - 从固有类型派生出来的含义
  - 在语境中的角色派生出来的含义

- 类型声明了实体的种类(如对象、属性、参数)
- 角色描述了实体在语境(如类、构件、协作、组合结构)中的含义

![](img/32b9da3a6e0f048e7dd2e9664c939f9e_106_0.png)

## 扩展机制

- 构造型(stereotypes)
  - 基于已有的建模元素引入新的建模元素
- 标记值(tagged value)
  - 扩展UML构造型的特性，可以用来创建构造型的详述信息
- 约束(constraint)
  - 扩展UML构造块的语义，可以用来增加新的规则或修改现有的规则
- 外廓(profile)
  - 提供了一组预定义的构造型、标记值、约束和基类，以用于特定领域的建模

## 示例：扩展机制

![](img/32b9da3a6e0f048e7dd2e9664c939f9e_108_0.png)

## 构造型(stereotypes)

### 构造型(stereotypes, 衍型)

- 根据已有的模型元素定义一个新元素
- 建立在UML已定义的模型元素基础上
- 可以用于所有的UML模型元素，如类、关联、用例、构件等
- UML规范提供了一些预定义的构造型

## 构造型的几种表现形式

![](img/32b9da3a6e0f048e7dd2e9664c939f9e_110_0.png)

## OMG提供的Profile

OMG基于Profile机制扩展UML应用

- SoaML (Service oriented architecture Modeling Language)
- SysML (OMG Systems Modeling Language)
- EAI (UML Profile for Enterprise Application Integration)
- MARTE (UML Profile for Modeling and Analysis of Real-time and Embedded Systems)
- UML Profile for System on a Chip (SoC)
- UML Testing Profile
- ……

## 外廓图（Profile Diagram）

UML2.2新增的Profile Diagram专门用于可视化描述外廓以及构造型、标记值、约束等

### 主要概念

- **Profile:** 一个包，代表一个外廓
- **Stereotype:** 定义一种针对元类的扩展
- **Metaclass:** 可被扩展的元素
- **Extension:** 构造型和元类之间的关系
- **ProfileApplication:** Profile和应用模型之间的关系

## 应用Profile Diagram

![](img/32b9da3a6e0f048e7dd2e9664c939f9e_114_0.png)

## 架构：4+1视图(from RUP)

Logical View
Implementation View
Use-Case View
Process View
Deployment View
Analysts/Designers
Structure
End-user
Functionality
Programmers
Software management
System integrators
Performance
Scalability
Throughput
System engineering
System topology
Delivery, installation communication

## 4+1视图(续)

### Use Case View

- End-user: Functionality

这些视图由用例视图所统一，它描述项目干系人（stakeholder）的需求；所有其他视图都是从用例视图派生而来，该视图把系统的基本需求捕获为用例并提供构造其他视图的基础

### Logical View

- Analysts/Designers: Structure

系统功能和词汇；描述问题域的词汇，作为类和对象的集合。重点是展示对象和类是如何组成系统、实现所需系统行为

