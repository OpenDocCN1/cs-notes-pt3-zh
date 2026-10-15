
- select：σ_p(r) = {t | t ∈ r and p(t)}

- project：$\Pi_{A_1,A_2,\dots,A_k}(r)$

- Cartesian product：×
  r × s = {t q | t ∈ r and q ∈ s}

将多个 relation 组合（join）在一起。

## 关系代数

Additional operations

- Set intersection ∩

  E₁ ∩ E₂ = E₁ - (E₁ - E₂)

- Natural join ⋈（自然连接）

  r ⋈ s = Π<sub>schema(r) ∪ schema(s)</sub> σ<sub>r.a₁=s.a₁ ∧ r.a₂=s.a₂ ∧ ...</sub> (r × s)

  schema(r) ∩ schema(s) = (a₁, a₂, ...)
  （属性的交集上取等值）

  - 试列出选过课程的学生学号、姓名
  - 试列出没有选课记录的学生学号、姓名

- Theta join ⋈<sub>θ</sub> or ×<sub>θ</sub>（条件连接）

  r ⋈<sub>θ</sub> s = σ<sub>θ</sub>(r × s)

- Outer join ⟗ 外连接，匹配连接及不匹配连接

  - 左外
  - 右外
  - 全外
  - 所有学生的选课情况
  - 所有课程的被选情况

- Assignment 赋值

  p ← r ⋈ s
  insert r ← r ∪ t₁
  delete r ← r - t₁

## Aggregate Functions and Operations

- **Aggregation function (聚集函数)** takes a collection of values and returns a **single value** as a result.

- avg: average value
- min: minimum value
- max: maximum value
- sum: sum of values
- count: number of values

- Null，不参与
- for r(a,b)：
  - sum(a) - sum(b) = sum(a - b)?
  - count(*), count(a), count(b)?
- count(name), count(distinct name)?

## SQL

(Structured Query Language)

## History

- IBM Sequel language developed as part of System R project at the IBM San Jose Research Laboratory
- Renamed Structured Query Language (SQL)
- ANSI and ISO standard SQL:
  - SQL-86 (First formalized by ANSI)
  - SQL-89 (integrity constraints)
  - SQL-92 (Major revision)
  - SQL:1999 (language name became Y2K compliant! ORDB)
  - SQL:2003, SQL:2006 (XML)
  - SQL:2008 (INSTEAD OF, TRUNCATE)
  - SQL:2011 (temporal databases)
- Commercial systems offer most, if not all, SQL-92 features, plus varying feature sets from later standards and special proprietary features.

## 数据库交互工具

- **Oracle**
  - SQL*Plus (command line)
  - iSQL*Plus (Web-based)
- **SQL Server**
  - SQLCMD (command line)
  - iSQL, OSQL
- **SQL Anywhere**
  - Dbisqlc (command line style)
  - Dbisql (GUI)
- **MySQL**
  - mysql (command line)

## SQL

- DDL
  - For Schema
  - Create, Alter, Drop
- DML
  - For Data
  - Modification: Insert, Update, Delete
  - Query: Select
  - Authorization: Grant, Revoke

## ODBC: Architecture

- Application
- ODBC driver manager
- ODBC driver
- DBMS

- Windows ODBC
- UnixODBC
- iODBC

![](img/5285b20d8f5a79969a3f150d38beebfc_51_0.png)

## ODBC: DSN

- DSN (Data Source Name) is a symbolic name that represents the ODBC connection.
- It stores the connection details like database name, directory, database driver, UserID, password, etc. when making a connection to the ODBC.

## DDL

For Schema (Create/Alter/Drop)

```sql
Create table Student(
  sno      char(10) primary key,
  sname    varchar(10),
  age      smallint check(age>=0),
  gender   char(1),
  dept     char(2)
);
```

```sql
Alter table student add GPA int;
Alter table student drop GPA;

Drop table student;
```

## DDL: data type

- **char(n)**
  - Fixed length character string, with user-specified length n.
- **varchar(n)**
  - Variable length character strings, with user-specified maximum length n.
- **Int**
  - Integer (a finite subset of the integers that is machine-dependent).
- **Smallint**
  - Small integer (a machine-dependent subset of the integer domain type).
