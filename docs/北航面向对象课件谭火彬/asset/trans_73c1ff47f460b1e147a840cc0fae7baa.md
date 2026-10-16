

## 模式的形式（模板）

- ☑ 名字
  - 作为模式的标识或句柄
- ☑ 问题
  - 陈述问题，描述模式的意图与目标
- ☑ 背景
  - 描述模式中问题及其解决方案可重现的前提，决定了模式的可应用性
- ☑ 影响力
  - 描述相关的因素与约束，以及它们与设计目标之间的交互与冲突
  - 揭示了问题复杂性，并定义了不同设计结果的折衷

## 模式的形式（续）

- ☑ 解决方案
  - ♦ 描述了解决问题的静态关系与动态规则
  - ♦ 还可描述注意事项以及模式的变形和特化
- ☑ 例子
- ☑ 结果
  - ♦ 运用模式后得到的系统状态或配置
- ☑ 基本原理
- ☑ 相关模式
- ☑ 已知应用

## 模式简史-1

1964 Christopher Alexander出版了Notes on the Synthesis of Form，该书尝试从一个不同的角度来看建筑的过程

1977 Christopher Alexander出版了A Pattern Language一书

1987 Ward Cunningham和Kent Beck开始将一些建筑学概念应用到使用SmallTalk语言的软件开发中

1992 Jim Coplien出版了Advanced C++: Programming Style and Idioms一书，将模式引入到程序设计领域

1992 Peter Coad在ACM上发表了他在分析模式方面的研究成果

1993 Erich Gamma的博士论文以及John Vlissides、Ralph Johnson和Richard Helm的其它研究成果在ECOOP 93上发表

1993 Kent Beck、Grady Booch、Jim Coplien以及其他人组成了Hillside小组，提供一个讨论模式的论坛

## 模式简史-2

1994 第一次编程模式语言（Pattern Language of Programming, PLoP）大会举行

1994 Design Patterns: Elements of Reusable Object-Oriented Software出版，使模式在设计领域得到广泛应用

1996 Frank Buschmann与其他人合作出版了Pattern-Oriented Software Architecture: A System of Patterns一书

1997 Martin Fowler出版了Analysis Patterns: Reusable Object Models一书，将模式引入分析领域

1999 Martin Fowler与其他人合作出版了Refactoring: Improving the Design of Existing Code一书

......

## 设计模式

☑什么是设计模式？

- 设计就是解决方案—对某个问题的解决
- 如果某个解决方案对某类问题都很有用
- 这时就把它总结出来
- 这就产生了设计模式

## 设计模式

- ☑ 是：
  - ◆ 优秀的设计范例
  - ◆ 从优秀设计方案中发现和总结出来的经验
  - ◆ 在实践中反复出现的设计问题的优秀解决方案
  - ◆ 设计者相互交流的基本术语： 设计语言
  - ◆ 培养优秀设计师的一条捷径
- ☑ 不是：
  - ◆ 面向对象设计的框架
  - ◆ 可供简单组合的设计元件
  - ◆ 发明创造出来的创新思路
  - ◆ 解决面向对象设计问题的完整方案

## 设计模式相关术语

- ☑ 设计模式 vs 模式
- ☑ 设计模式 vs 设计原则
- ☑ 设计模式 vs 软件体系结构
- ☑ 设计模式 vs 习惯用法

## 设计模式 vs 模式

- 模式的含义更广，可用于各类背景
  - 设计模式是一种模式
  - 除设计模式外，在软件领域还有其他的模式
    - 分析模式、组织模式、过程模式、领域模式
- 设计模式是关于面向对象设计微结构的模式
  - 这种微结构又称为对象结构
  - 微结构指对象及其类之间的静态或动态关系

## 设计模式 vs 设计原则

- ☑ 设计原则是面向对象设计的指导思想
  - ◆ 设计模式只是更好地遵循这一指导思想的手段之一
- ☑ 设计模式是面向对象设计的具体技术
  - ◆ 设计模式抽象出成功设计的共性，并进行分类与标识
  - ◆ 设计模式通过描述对象、协作和职责将设计中的意图抽取出来

## 设计模式 vs 软件体系结构

- 软件体系结构所研究的对象粒度更大
  - 软件体系结构可以是为单个应用而设计
  - 设计模式通常是为了多个软件产品的生产线而设计
- 某些专家也将软件体系结构看作抽象层次更高的模式
  - 体系结构模式（宏模式）、设计模式（微模式）与习惯用法三个层次

## 设计模式 vs 习惯用法

☑ 习惯用法（idiom）所讨论的对象粒度更小

- 习惯用法通常是与特定的程序设计语言有关
- 设计模式通常只与特定的程序设计方法有关

☑ 习惯用法可看作抽象层次更低的模式

## 内容安排

- 模式与设计模式
- **GoF设计模式及应用**
- **GRASP**职责分配模式
- 模式与编程语言
- 模式与重构

## GoF设计模式

- 时间
  - 1994
- 人物
  - Erich Gamma、John Vlissides、Ralph Johnson、Richard Helm
  - 合称GoF (Gang of Four)
- 事件
  - Design Patterns: Elements of Reusable Object-Oriented Software (设计模式-可复用面向对象软件的基础) 的出版
  - 提出23种设计模式，统称为GoF模式

## GoF模式分类-1

☑ 根据模式的目的(用来完成什么工作的)

- 创建型模式
- 结构型模式
- 行为型模式

☑ 根据模式的作用范围(是处理类还是处理对象的):

- 类模式
- 对象模式

## GoF模式分类-2

- ☑ 创建型模式
  - 创建型类模式将对象的部分创建工作延迟到子类
  - 创建型对象模式将它延迟到另一个对象中
- ☑ 结构型模式
  - 结构型类模式使用继承机制来组合类
  - 结构型对象模式描述了对象间的组装方式
- ☑ 行为型模式
  - 行为型类模式使用继承描述算法与控制法
  - 行为型对象模式则描述一组对象怎样协作完成单个对象无法完成的工作

## GoF设计模式

### GoF 23种设计模式

| | 创建型 | 结构型 | 行为型 |
|---|---|---|---|
| 类 | Factory Method | Adapter (Class) | Interpreter<br>Template Method |
| 对象 | Abstract Factory<br>Builder<br>Prototype<br>Singleton | Adapter (Object)<br>Bridge<br>Composite<br>Decorator<br>Facade<br>Flyweight<br>Proxy | Chain of Responsibility<br>Command<br>Iterator<br>Mediator<br>Memento<br>Observer<br>State<br>Strategy<br>Visitor |

## 创建型模式

- ☑ 1 工厂方法 factory method
  - 定义一个用于创建对象的接口，让子类决定实例化哪一个类
- ☑ 2 抽象工厂 abstract factory
  - 提供一个接口，不必指定具体类即可创建一族相关的或相依赖的对象
- ☑ 3 生成器 builder
  - 将一个复杂对象的构造与它的表示分离，从而同一构造过程可以创建不同的表示
- ☑ 4 原型 prototype
  - 利用一个原型实例指定创建对象的类别，从而创建该原型的新的对象副本
- ☑ 5 单例 singleton
  - 保证一个类只有一个实例，并提供访问它的一个全局访问点

## 结构型模式

- ☑ 6 适配器 adapter
  - ◆ 将一个类的接口转换成客户希望的另外一个接口，使接口不兼容的类可以互相工作
- ☑ 7 桥 bridge
  - ◆ 将抽象部分与实现部分分离，使之可以独立的变化
- ☑ 8 组合 composite
  - ◆ 将对象组合成树型结构表示“部分-整体”层次结构，允许客户程序以统一方式处理单个对象与组合对象
- ☑ 9 装饰 decorator
  - ◆ 动态地给一个对象增加附加职责

