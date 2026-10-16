
## Difference Between an Abstract Class and a Concrete Class

## Concrete class (实体类)

- Can be used by other classes to create objects
- Can be inherited by its subclasses

## Abstract class (抽象类)

- **Can not** be used by other classes to create objects
- Can be inherited by its subclasses

## Form of a Class Hierarchy

Ideally, a class hierarchy has the following form

![](img/95717dc23f76db2057b9aa0c49790307_141_0.png)

![](img/95717dc23f76db2057b9aa0c49790307_142_0.png)

The leaves are concrete classes

## Java Interface

## Java Interface(Java接口)

- 什么叫做Java接口?
- Java interface is a collection of characteristics of methods
  public interface Account {
    public abstract deposit (double amt);
    public abstract withdraw (double amt);
    public abstract transfer(double amt);
  }

## Java Interface(**Java 接口**)

## Properties of Java interface:

- A Java interface
  - Has no constructor (**不允许有构造函数**)
  - One Java interface can have many very different implementations
  - A Java class can **implement** as many Java interfaces as one wants

## Java Interface(Java 接口)

![](img/95717dc23f76db2057b9aa0c49790307_146_0.png)

One Java interface can have many very different implementations

## Java Interface(Java接口)

## Why use interface?

- 1) 重复利用 For reuse purpose, an interface can define a set of related functions for some special use
- 2) 声明类型 An interface can be used to claim a type, with its different subclasses to implement its functions. The purpose is to realize dynamic binding
- 3) 代表某个协议 A language environment may need a protocol to do something special and so need an interface, e.g., java interface Runnable must be implemented whenever a programmer wants to write a multithread program

## Java Interface(Java接口)

Code for dynamic binding:

```
Account act
if(usrChoice == 1)
    act = new CheckingAccount ();
else if(usrChoice == 2)
    act = new SavingsAccount ();
else if(usrChoice == 3)
    act = new OnlineAccount ();
act.deposit(500.23)
```

## Java Interface(Java接口)

**Example:** from Java API

```
Public interface Runnable{
    Public abstract void run( )
}
```

public interface Runnable. The Runnable interface should be implemented by any class whose instances are intended to be executed by a thread. This interface is designed to provide a common protocol for objects that wish to execute code while they are active. For example, Runnable is implemented by class Thread.

## Object Oriented Design principles

## Design Principles

- 1) Interface segregation principle
  ➢ To avoid Interface contamination
- 2) Open-closed principle
  ➢ Open for extension
  ➢ Closed for modification
- 3) Dependency inversion Principle
  ➢ In traditional procedural system design, higher level depends on Lower level
  ➢ In OO design,
    • Advanced business logic depends on the interface, Program to an interface, not an implementation ;
    • Abstraction should not depend upon details. Details should depend upon Abstractions

## 1. Interface segregation principle

## Example of interface
contamination

![](img/95717dc23f76db2057b9aa0c49790307_153_0.png)

This class contains 12 methods, some of them are unrelated, which means that this is an contaminated interface

![](img/95717dc23f76db2057b9aa0c49790307_154_0.png)

According to functionalities, separate the original interface into several classes, i.e., follows the Interface segregation principle

## 2. Open/closed principle

- **Open/closed principle** (开闭原则)
- Open for extension, and closed for modification
- **在面向对象编程中，开/闭原则声称“软件实体（类）应该对扩展开放，但是对修改关闭”，也就是说这样一个实体可以允许其行为被扩展或修改而不改变它的源代码。**

## 3. Dependency inversion principle

![](img/95717dc23f76db2057b9aa0c49790307_156_0.png)

In traditional procedural system design, higher level depends on Lower level
