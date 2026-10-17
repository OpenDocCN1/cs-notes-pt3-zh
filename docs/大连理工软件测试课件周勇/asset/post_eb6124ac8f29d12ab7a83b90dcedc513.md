

# 面向对象的测试

## 面向对象的软件特征

- 软件缺陷可能不能修复
  - 没有足够的时间
  - 不算真正的软件缺陷
  - 修复的风险太大
  - 不值得修复

- 审查软件缺陷，判定是否可以修复
- 判定依据是软件测试的缺陷报告

## Object Orientation的原理

Object Orientation

- Abstraction
- Encapsulation
- Modularity
- Hierarchy

## 封装 Encapsulation

➢ Hide implementation from clients

❧ Clients depend on interface

Improves Resiliency

## 层次Hierarchy

### Levels of abstraction

Increasing abstraction

Decreasing abstraction

Bank Account

Security

Real Estate

Savings

Checking

Stock

Bond

Elements at the same level of the hierarchy should be at the same level of abstraction

## Object Orientation中的概念

- Object
- Class
- Attribute
- Operation
- Interface (Polymorphism)
- Component
- Package
- Relationships

## 对象 Object

Informally, an object represents an entity, either physical, conceptual, or software

- Physical entity

- Conceptual entity

- Software entity

## 对象的正式定义

- An object is a concept, abstraction, or thing with sharp boundaries and meaning for an application
- An object is something that has:
  - State
  - Behavior
  - Identity

## 对象表示

➢ An object is represented as rectangles with underlined names

Class Name Only

Object Name Only

Class and Object Name

Professor Clark

> _(stay tuned for classes)_

## 类Class

- A class is a description of a group of objects with common properties (attributes), behavior (operations), relationships, and semantics
  - An object is an instance of a class
- A class is an abstraction in that it:
  - Emphasizes relevant characteristics
  - Suppresses other characteristics

*OO Principle: Abstraction*

## 类举例

# Class

Course

**Properties**
- Name
- Location
- Days offered
- Credit hours
- Start time
- End time

**Behavior**
- Add a student
- Delete a student
- Get course roster
- Determine if it is full

## 类的表示

➢ A class is represented using a compartmented rectangle

| Professor |
|---|
| |
| |

Professor Clark

## 类的组成

- A class is comprised of three sections
  - The first section contains the class name
  - The second section shows the structure (attributes)
  - The third section shows the behavior (operations)

## 对象的类

### How many classes do you see?

## 类和对象之间的关系

### A class is an abstract definition of an object

- It defines the structure and behavior of each object in the class

- It serves as a template for creating objects

### Objects are grouped into classes

Professor Smith

Professor Mellon

Professor Jones

## 操作 Operation

