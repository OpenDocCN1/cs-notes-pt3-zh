
## E-R Diagram With Aggregation

![](img/5b3fa86b6571b68f1313de4e5d81fe8a_386_0.png)

## Summary of Symbols Used in E-R Notation

| Symbol | Description | Symbol | Description |
|--------|-------------|--------|-------------|
| E | Entity Set | A | Attribute |
| E | Weak Entity Set | A | Multivalued Attribute |
| R | Relationship Set | A | Derived Attribute |
| R | Identifying Relationship Set for Weak Entity Set | R-E | Total Participation of Entity Set in Relationship |
| A | Primary Key | A | Discriminating Attribute of Weak Entity Set |

## Summary of Symbols (Cont.)

| Symbol | Meaning |
|---|---|
| R in a diamond with no arrows | Many to Many Relationship |
| R in a diamond with an arrow toward the entity | Many to One Relationship |
| R in a diamond with arrows on both sides | One to One Relationship |
| R connected to E with `1..h` | Cardinality Limits |
| R connected to E with `role-name` | Role Indicator |
| ISA | ISA (Specialization or Generalization) |
| ISA with double line | Total Generalization |
| ISA with `disjoint` | Disjoint Generalization |

## Alternative E-R Notations

Entity set E with attributes A1, A2, A3 and primary key A1

| E |
|---|
| A1 |
| A2 |
| A3 |

Many to Many Relationship

* R *

R

One to One Relationship

1 R 1

R

Many to One Relationship

* R 1

R

## 6.7 Design of an E-R database schema (1) the steps of database design

### a) Requirement analysis

- What data, applications, and operations needed

### b) Conceptual database design:

- A high-level description of data, constraints using E-R model or a similar high level data model

### c) Logical database design: (6.9)

- Convert the conceptual design into DB schema --- tables

- **Schema refinement: Normalization of relations**: Check relational schema for redundancies and related anomalies.

### d) Physical database design:

- Indexing, clustering and database tuning

补充：

## 数据库的设计步骤

![](img/5b3fa86b6571b68f1313de4e5d81fe8a_391_0.png)

## 补充：

- 需求分析
- 概念结构设计
  - 设计局部视图
  - 设计集成视图
- 逻辑结构设计
  - 设计逻辑结构
  - 优化逻辑模型
- 物理结构设计
  - 设计物理结构
  - 评价物理结构
- 数据库实施
  - 物理实现
  - 试运行（加载试验数据）
- 数据库运行维护

### 目标组织

**结构设计**

- 数据分析
- 概念模型设计
- 逻辑模型设计
- 子模式设计
- 物理模型设计
- 加载试验数据
- 功能、性能考核
- N
- 满意？
- 加载数据库
- 运行、维护

**行为设计**

- 行为分析（用户业务活动分析）
- 功能模型，功能说明
- 事务处理设计（概要设计）
- 应用程序设计（详细设计）
- 应用程序编码
- 程序调试和试运行

## 数据库系统开发步骤

### (2) Some E-R Design consideration

**1) Use an attribute or entity set to represent an object?**

e.g.: (a) employee(emp-id, emp-name, ..., phone)

优点：简单。但多个电话怎么处理？ 电话的其他属性？

or, (b) employee(emp-id, emp-name, ...);

phone(phone-num, location, type, color);

emp-phone(emp-id, phone-num)

- 若一个对象只对其名字及单值感兴趣，则可作为属性，如 性别；若一个对象除名字外，本身还有其他属性需描述，则该对象应定义为实体集。如 电话，住址，部门
- 一个对象不能同时作为实体和属性。
- 一个实体集不能与另一实体集的属性相关联，只能实体与实体相联系。

## E-R Design Decisions(cont.)

### 3） Use it as an attribute of an entity or a relationship? e.g.

student(sid, name, sex, age, ..., supervisor-id, supervisor-name, supervisor-position, ..., class, monitor)

- 要从对象的语义独立性和减少数据冗余考虑
  - student(sid, name, sex, age, ...);
  - supervisor(sup-id, name, position, ...);
  - stu-sup(sid, sup-id, from, to);
  - class(classno, specialty, monitor, stu-num);
  - stu-class(sid, classno);

## (3) Example1: Design of Banking Database

- Get system requirements
  - Branch, customer, employee, loan
  - Account: saving account, checking account
- Entity sets design
  - Branch(branch-name, branch-city, assets);
  - Customer(cust-id, cust-name, cust-street, cust-city),
  - Employee(emp-id, emp-name, phone, salary),
  - Account(acc-number, balance),
    saving-acc(interest-rate),
    checking-acc(overdraft-amount)
  - Loan(loan-number, amount),
    payment(pay-number, pay-date, pay-amount)

## Relationship sets design

- Borrower: customer -- loan
- Depositor: account – customer (account-date)
- Loan-branch: loan → branch
- account-branch: account → branch
- Cust-banker: customer → employee (type)
- Works-for: manager ← worker

## E-R diagram
