# Postgres数据库实现原理：P4：系统目录

![](img/bc75b94c830c0ff14c4bc3a74a766963_1.png)

在本节课中，我们将要学习PostgreSQL如何管理其内部的各种对象，例如数据库、表、视图、函数等。核心在于理解**系统目录**，它是一组特殊的表，用于存储数据库的元数据。

## 系统目录的作用

上一节我们介绍了PostgreSQL中的基本对象。本节中我们来看看这些对象是如何被系统管理和表示的。

![](img/bc75b94c830c0ff14c4bc3a74a766963_3.png)

![](img/bc75b94c830c0ff14c4bc3a74a766963_5.png)

![](img/bc75b94c830c0ff14c4bc3a74a766963_7.png)

系统目录是PostgreSQL用来记录所有数据库对象信息的内部表。例如，有一个目录表记录了存在哪些数据库、它们的所有者以及访问控制权限。类似地，也有目录表用于记录模式、表空间、表、属性、约束、视图、存储过程、触发器和规则。

![](img/bc75b94c830c0ff14c4bc3a74a766963_9.png)

大多数对象都有名称，并且几乎都有一个唯一的对象标识符，即**OID**。

![](img/bc75b94c830c0ff14c4bc3a74a766963_11.png)

## OID与目录表的关系

![](img/bc75b94c830c0ff14c4bc3a74a766963_12.png)

![](img/bc75b94c830c0ff14c4bc3a74a766963_14.png)

![](img/bc75b94c830c0ff14c4bc3a74a766963_16.png)

以下是关于OID和目录表交互的关键点：

![](img/bc75b94c830c0ff14c4bc3a74a766963_18.png)

*   **OID的可见性**：并非所有表的OID都默认可见。例如，用户创建的表可能没有OID列，除非特别指定。但系统目录表本身通常包含OID。
*   **目录表引用**：目录表之间的外键引用通常指向另一个目录表中元组的OID值。例如，`pg_database`表中的`datdba`字段（数据库所有者）就是一个OID，它引用了`pg_authid`（角色表）中的一个条目。
*   **查询处理的基础**：当执行SQL查询（如`SELECT * FROM students;`）时，查询处理器必须查阅目录表来验证`students`表是否存在、位于哪个模式、包含哪些属性等元信息。

![](img/bc75b94c830c0ff14c4bc3a74a766963_20.png)

![](img/bc75b94c830c0ff14c4bc3a74a766963_21.png)

![](img/bc75b94c830c0ff14c4bc3a74a766963_23.png)

![](img/bc75b94c830c0ff14c4bc3a74a766963_24.png)

系统目录表在PostgreSQL中通常以`pg_`为前缀，例如`pg_class`表存储了关于表和类似对象（“关系”）的信息。

![](img/bc75b94c830c0ff14c4bc3a74a766963_26.png)

![](img/bc75b94c830c0ff14c4bc3a74a766963_27.png)

![](img/bc75b94c830c0ff14c4bc3a74a766963_29.png)

![](img/bc75b94c830c0ff14c4bc3a74a766963_30.png)

## 标准目录与PostgreSQL特定目录

![](img/bc75b94c830c0ff14c4bc3a74a766963_32.png)

关于目录标准，有以下需要注意的方面：

*   **历史原因**：标准化的目录模式（如SQL标准中的`INFORMATION_SCHEMA`）在2000年左右才出现。而像PostgreSQL这样的数据库出现得更早，因此它们拥有自己特定的目录结构。
*   **两种视图**：
    *   `pg_catalog`：这是PostgreSQL原生的系统目录模式。
    *   `information_schema`：这是一组按照SQL标准定义的视图，它们底层基于`pg_catalog`中的表。使用`information_schema`可以提高应用程序在不同数据库系统间的可移植性。

![](img/bc75b94c830c0ff14c4bc3a74a766963_34.png)

## 目录的维护与更新

目录表本身也需要被更新。这种更新发生在执行数据定义语言操作时。

![](img/bc75b94c830c0ff14c4bc3a74a766963_36.png)

![](img/bc75b94c830c0ff14c4bc3a74a766963_38.png)

![](img/bc75b94c830c0ff14c4bc3a74a766963_39.png)

![](img/bc75b94c830c0ff14c4bc3a74a766963_41.png)

以下是触发目录变更的几种主要操作：

![](img/bc75b94c830c0ff14c4bc3a74a766963_43.png)

![](img/bc75b94c830c0ff14c4bc3a74a766963_45.png)

![](img/bc75b94c830c0ff14c4bc3a74a766963_47.png)

1.  **创建对象**：当使用`CREATE TABLE`或`CREATE TYPE`等语句时，系统会在相应的目录表中插入新记录。
2.  **删除对象**：当使用`DROP TABLE`等语句时，系统会从目录表中删除对应的记录。
3.  **修改对象**：当使用`ALTER TABLE`等语句时，系统会更新目录表中的相应记录。
4.  **权限管理**：当使用`GRANT`或`REVOKE`语句时，系统会更新与访问控制相关的目录表。

![](img/bc75b94c830c0ff14c4bc3a74a766963_49.png)

![](img/bc75b94c830c0ff14c4bc3a74a766963_51.png)

例如，当执行`DROP TABLE groups;`时，实际上是在`pg_class`等目录表中删除了与`groups`表相关的记录。

## 总结

![](img/bc75b94c830c0ff14c4bc3a74a766963_53.png)

![](img/bc75b94c830c0ff14c4bc3a74a766963_55.png)

本节课中我们一起学习了PostgreSQL系统目录的核心概念。我们了解到系统目录是一组存储所有数据库对象元数据的特殊表，它们使用**OID**作为对象间引用的主要机制。目录通过`pg_catalog`模式直接访问，同时也通过标准的`information_schema`视图提供兼容性。最后，我们看到了目录数据如何随着`CREATE`、`DROP`、`ALTER`等DDL命令而动态更新，这是数据库管理自身结构的基石。