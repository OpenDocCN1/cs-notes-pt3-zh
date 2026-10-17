

## 🛠️ create new domain

```sql
create domain Dollars as numeric(12, 2) not null;
create domain Pounds as numeric(12,2);
```

```sql
Create table employee
(
    eno char(10) primary key,
    ename varchar(15),
    job varchar(10),
    salary Dollars,
    comm Pounds
);
```

## The difference between create type and domain

- Domains can have constrains, such as not null, specified on them, and can have default value defined for variables of the domain type.
- Domains are NOT strongly typed, and the values of one domain type can be assigned to values of another domain type as long as the underlying types are compatible.

![](img/5b3fa86b6571b68f1313de4e5d81fe8a_250_0.png)

![](img/5b3fa86b6571b68f1313de4e5d81fe8a_250_1.png)

## Large-Object Types

Large objects (photos, videos, CAD files, etc.) are stored as a *large object*

- **blob:** binary large object - object is a large collection of uninterpreted binary data (whose interpretation is left to an application outside of the database system)
- **clob:** character large object - object is a large collection of character data
- When a query returns a large object, a **pointer is returned** rather than the large object itself.

![](img/5b3fa86b6571b68f1313de4e5d81fe8a_251_0.png)

![](img/5b3fa86b6571b68f1313de4e5d81fe8a_251_1.png)

![](img/5b3fa86b6571b68f1313de4e5d81fe8a_251_2.png)

## Catalogs (目录), schemas and environments

![](img/5b3fa86b6571b68f1313de4e5d81fe8a_252_0.png)

## 4.2 Integrity Constraints（完整性约束）

- Integrity constraints guard against accidental damage to the database, by ensuring that authorized changes to the database do not result in a loss of data consistency.
- A checking（核算）account must have a balance greater than $10,000.00
- A salary of a bank employee must be at least $4.00 an hour
- A customer must have a (non-null) phone number

- 域完整性、实体完整性（主键的约束）、参照完整性（外键的约束）和用户定义的完整性约束。
- 完整性约束是数据库实例(Instance)必须遵循的
- 完整性约束由DBMS维护

![](img/5b3fa86b6571b68f1313de4e5d81fe8a_253_0.png)

## 4.2 Integrity Constraints (cont.)

### Constraints on a Single Relation

- not null
- primary key
- unique
- check (`P`), where `P` is a predicate

```sql
create table branch2 (
    branch_name varchar (30) primary key,
    branch_city varchar(30),
    assets integer not null,
    check (assets >= 100) );
```

## 4.2.1 Referential Integrity （参照完整性约束）

- In Chapter 3 the concept was mentioned.
- Formal Definition

- Let \( r_1(R_1) \) and \( r_2(R_2) \) be relations with primary keys \( K_1 \) and \( K_2 \) respectively.

- The subset \( \alpha \) of \( R_2 \) is a **foreign key** referencing \( K_1 \) in relation \( r_1 \), if for every \( t_2 \) in \( r_2 \) there **must** be a tuple \( t_1 \) in \( r_1 \) such that \( t_1[K_1] = t_2[\alpha] \).

- Referential integrity constraint also called **subset dependency** since its can be written as \( \Pi_\alpha (r_2) \subseteq \Pi_{K_1} (r_1) \).

![](img/5b3fa86b6571b68f1313de4e5d81fe8a_256_0.png)

![](img/5b3fa86b6571b68f1313de4e5d81fe8a_256_1.png)

## (Recall from chapter 2 about foreign key)

Assume there exists relation r and s: r(A, **B**, C), s(**B**, D), we say attribute **B** is **foreign key** from relation r, and r is called *referencing relation* (参照关系), and s is called *referenced relation* (被参照关系).

- e.g.
  - ◆ 学生(学号, 姓名, 性别, **专业号**, 年龄) --参照关系
  - 专业(**专业号**, 专业名称) --被参照关系（目标关系）
  - 其中属性 **专业号** 称为关系 *学生* 的外码。

- ◆ Account(**account-number**, **branch-name**, balance) --参照关系
  - Branch(**branch-name**, branch-city, assets) --被参照关系

参照关系中外码的值必须在被参照关系中实际存在，或为 null。

## Checking Referential Integrity on Database Modification

The following tests must be made in order to preserve the following referential integrity constraint:

\(\Pi_\alpha (r_2) \subseteq \Pi_K (r_1) \quad \alpha \text{ in } r_2 \text{ is FK (Foreign Key)}\)

**Insert.** If a tuple \(t_2\) is inserted into \(r_2\), the system must ensure that there is a tuple \(t_1\) in \(r_1\) such that \(t_1[K] = t_2[\alpha]\). That is
\(t_2[\alpha] \in \Pi_K (r_1)\)

![](img/5b3fa86b6571b68f1313de4e5d81fe8a_258_0.png)

