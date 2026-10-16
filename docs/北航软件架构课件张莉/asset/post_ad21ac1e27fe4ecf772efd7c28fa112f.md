
# Behavioral Patterns （续）

- Mediator (273)
  - Define an object that encapsulates how a set of objects interact. Mediator promotes loose coupling by keeping objects from referring to each other explicitly, and it lets you vary their interaction independently.
- Memento (285)
  - Without violating encapsulation, capture and externalize an object's internal state so that the object can be restored to this state later.
- Observer (295)
  - Define a one-to-many dependency between objects so that when one object changes state, all its dependents are notified and updated automatically.
- State (305)
  - Allow an object to alter its behavior when its internal state changes. The object will appear to change its class.

# Behavioral Patterns （续）

- Strategy (315)
  - Define a family of algorithms, encapsulate each one, and make them interchangeable. Strategy lets the algorithm vary independently from clients that use it.
- Template Method (325)
  - Define the skeleton of an algorithm in an operation, deferring some steps to subclasses. Template Method lets subclasses redefine certain steps of an algorithm without changing the algorithm's structure.
- Visitor (331)
  - Represent an operation to be performed on the elements of an object structure. Visitor lets you define a new operation without changing the classes of the elements on which it operates.

# For Every Pattern

- Pattern Name and Classification
- Intent（目的）
- Also Known As（别名）
- Motivation（问题的提出）
- Applicability（什么情况下使用）
- Structure（结构）
- Participants（元素）
- Collaborations —How the participants collaborate to carry out their responsibilities.

- Consequences —How does the pattern support its objectives? What are the trade-offs and results of using the pattern? What aspect of system structure does it let you vary independently?
- Implementation —What pitfalls, hints, or techniques should you be aware of when implementing the pattern? Are there language-specific issues?
- Sample Code —in C++ or Smalltalk.
- Known Uses
- Related Patterns —What design patterns are closely related to this one? What are the important differences? With which other patterns should this one be used?

# Creational Patterns

• 创建型模式处理对象的创建过程，从而使系统结构独立于对象的创建、组合和表达。类创建型模式使用继承来改变对象的类型，而对象创建型模式则将对象的实例化交给其它对象。

• 在该模式中不断出现的主题。
  —该模式解决了相互依赖的对象。
  —隔离了如何将对象组成整体的复杂性。

• 对于对象，系统提供了创建对象的特定定义接口。创建性模式在所创建的对象、创建人、创建方法时间和上提供了解耦性，从而可用用户结构上、功能上不同的对象来配置系统，配置可以是静态的，也可以是动态的。

# Creational Patterns

Abstract Factory: provide an interface for creating families of related or dependent objects without specifying their concrete classes.

![](img/da691714eec1b93795825838a75ee408_26_0.png)

# Abstract Factory

- **何时用：**
  - a system should be independent of how its products are created, composed, and represented.
  - a system should be configured with one of multiple families of products.
  - a family of related product objects is designed to be used together, and you need to enforce this constraint.
  - you want to provide a class library of products, and you want to reveal just their interfaces, not their implementations.

# Abstract Factory

- **结构**

![](img/da691714eec1b93795825838a75ee408_27_0.png)

# Abstract Factory

- **Consequences**
  1. It isolates concrete classes.
  2. It makes exchanging product families easy.
  3. It promotes consistency among products.
  4. Supporting new kinds of products is difficult.

# Creational Patterns

# Builder

- Separate the construction of a complex object from its representation so that the same construction process can create different representations.

# Builder

- **来源**

![](img/da691714eec1b93795825838a75ee408_27_1.png)

# Builder

- 何时用：
  - the algorithm for creating a complex object should be independent of the parts that make up the object and how they're assembled.
  - the construction process must allow different representations for the object that's constructed.

![](img/da691714eec1b93795825838a75ee408_27_2.png)
