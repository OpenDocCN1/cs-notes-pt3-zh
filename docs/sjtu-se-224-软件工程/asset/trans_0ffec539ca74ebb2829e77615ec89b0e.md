

## N-S图示例

![](img/bd1e40ee9d51e0bf88db831d8e65a09d_91_0.png)

## 问题分析图(PAD)

![](img/bd1e40ee9d51e0bf88db831d8e65a09d_91_1.png)

## PAD示例

![](img/bd1e40ee9d51e0bf88db831d8e65a09d_91_2.png)

## PDL (Program Design Language)

- PDL是一种用于描述功能模块的算法设计和加工细节的语言。称为设计程序语言。它是一种伪码。
- 伪码的语法规则分为“外语法”和“内语法”。
- PDL具有严格的关键字外语法，用于定义控制结构和数据结构，同时它的表示实际操作和条件的内语法可使用自然语言的词汇。

## 示例: 拼写检查程序

```
PROCEDURE spellcheck IS
BEGIN
split document into single words
look up words in dictionary
display words which are not in dictionary
create a new dictionary
END spellcheck
```

## 软件工程

## Module: 面向对象设计

上海交通大学软件工程中心

## Agenda

- OO Design Overview
- The Principles of Object-Oriented Design
- Architectural Design
- Component Design
- Class Design
- From Design to Implementation

## 软件工程概论

Introduction to Software Engineering

## OO DESIGN OVERVIEW

## Understanding Design

- A process that uses the products of analysis to produce a specification for implementing a system.
- A logical description of how a system will work.
- Emphasizes a conceptual solution (in software and hardware) that fulfills the requirements, rather than its implementation.
- “do the right thing (analysis), and do the thing right (design)”

## Analysis Versus Design

### Analysis

- Focus on understanding the problem
- Idealized design
- Behavior
- System structure
- Functional requirements
- A small model

### Design

- Focus on understanding the solution
- Operations and attributes
- Performance
- Close to real code
- Object lifecycles
- Nonfunctional requirements
- A large model

## Object Oriented Design

- The specification of a logical software solution in terms of software objects,
  - such as their classes, attributes, methods, and collaborations.
- During object-oriented design (or simply, object design) there is an emphasis on defining software objects and how they collaborate to fulfill the requirements.

## 软件工程概论

Introduction to Software Engineering

## THE PRINCIPLES OF OBJECT-ORIENTED DESIGN

## SRP: The Single – Responsibility Principle

### Separating Coupled Responsibilities

![](img/bd1e40ee9d51e0bf88db831d8e65a09d_101_0.png)

## SRP: The Single – Responsibility Principle

### Separating Coupled Responsibilities

![](img/bd1e40ee9d51e0bf88db831d8e65a09d_102_0.png)

## LSP: The Liskov Substitution Principle

### The Liskov Substitution Principle

- subtypes must be substitutable for their base types
  - SubClass can be used instead of parent Class
- If for each object o1 of type S there is an object o2 of type T such that for all programs P defined in terms of T, the behavior of P is unchanged when o1 is substituted for o2 then S is a subtype of T [Liskov88].
  - If using implementation of T or subclass of T to be used instead of T, Software P which is associated with type T(interface or abstract class) can work well.
- Essential: the objects which is in the same inherit architecture should have behavior features.

### Example:

- In real world, penguin and bird is a “is-a” relationship. If we design penguin is a subclass of bird class, we violate LSP principle. because bird can fly() while penguin can not fly. So how to change this design?

## LSP: The Liskov Substitution Principle

![](img/bd1e40ee9d51e0bf88db831d8e65a09d_104_0.png)

![](img/bd1e40ee9d51e0bf88db831d8e65a09d_104_1.png)

## DIP: The Dependency Inversion Principle

- The Dependency Inversion Principle
  - High-level modules should **not** depend on low-level modules.
    - Both should depend on abstractions
  - Abstraction should **not** depend on details
    - Details should depend on abstractions
- Example

![](img/bd1e40ee9d51e0bf88db831d8e65a09d_105_0.png)

## DIP: The Dependency Inversion Principle

- Depend on Abstractions
- Naive model of a Button and a Lamp
- Dependency inversion applied to the Lamp

![](img/bd1e40ee9d51e0bf88db831d8e65a09d_106_0.png)

![](img/bd1e40ee9d51e0bf88db831d8e65a09d_106_1.png)

