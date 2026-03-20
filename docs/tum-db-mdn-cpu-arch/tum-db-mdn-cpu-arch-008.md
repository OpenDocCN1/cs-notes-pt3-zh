# 008：事务与恢复概述

![](img/edcedfaec63b0ada78f68ded050f8e0e_1.png)

![](img/edcedfaec63b0ada78f68ded050f8e0e_3.png)

![](img/edcedfaec63b0ada78f68ded050f8e0e_4.png)

![](img/edcedfaec63b0ada78f68ded050f8e0e_6.png)

![](img/edcedfaec63b0ada78f68ded050f8e0e_8.png)

![](img/edcedfaec63b0ada78f68ded050f8e0e_10.png)

![](img/edcedfaec63b0ada78f68ded050f8e0e_12.png)

![](img/edcedfaec63b0ada78f68ded050f8e0e_14.png)

![](img/edcedfaec63b0ada78f68ded050f8e0e_16.png)

在本节课中，我们将要学习数据库系统中的事务与恢复机制。事务是数据库提供原子性、一致性、隔离性和持久性（ACID）保证的核心概念，而恢复机制则确保系统在发生故障后能回到一致状态，且已提交的数据不会丢失。这两个概念在实现上紧密相连。

![](img/edcedfaec63b0ada78f68ded050f8e0e_18.png)

![](img/edcedfaec63b0ada78f68ded050f8e0e_19.png)

![](img/edcedfaec63b0ada78f68ded050f8e0e_21.png)

![](img/edcedfaec63b0ada78f68ded050f8e0e_23.png)

上一节我们介绍了多种外部存储的哈希索引方案。本节中，我们来看看数据库系统的另一个核心组成部分：事务处理。

![](img/edcedfaec63b0ada78f68ded050f8e0e_25.png)

![](img/edcedfaec63b0ada78f68ded050f8e0e_27.png)

![](img/edcedfaec63b0ada78f68ded050f8e0e_28.png)

![](img/edcedfaec63b0ada78f68ded050f8e0e_30.png)

## 事务的必要性

![](img/edcedfaec63b0ada78f68ded050f8e0e_32.png)

![](img/edcedfaec63b0ada78f68ded050f8e0e_33.png)

![](img/edcedfaec63b0ada78f68ded050f8e0e_35.png)

数据库系统提供事务支持，允许我们将一系列操作组合成一个复合操作。这个复合操作会以明确定义的语义执行。同时，数据库系统还提供恢复组件，确保即使在系统崩溃后，数据库也能处于一致状态，且已提交的数据永不丢失。

![](img/edcedfaec63b0ada78f68ded050f8e0e_37.png)

![](img/edcedfaec63b0ada78f68ded050f8e0e_39.png)

![](img/edcedfaec63b0ada78f68ded050f8e0e_40.png)

![](img/edcedfaec63b0ada78f68ded050f8e0e_41.png)

![](img/edcedfaec63b0ada78f68ded050f8e0e_43.png)

![](img/edcedfaec63b0ada78f68ded050f8e0e_45.png)

这两个概念紧密相关。例如，崩溃可能发生在一个复合操作的中间。我们必须确保，即使操作未完成，数据库在恢复后仍处于一致状态。事务的ACID属性正是为了解决这类问题。

![](img/edcedfaec63b0ada78f68ded050f8e0e_47.png)

![](img/edcedfaec63b0ada78f68ded050f8e0e_49.png)

![](img/edcedfaec63b0ada78f68ded050f8e0e_51.png)

![](img/edcedfaec63b0ada78f68ded050f8e0e_53.png)

![](img/edcedfaec63b0ada78f68ded050f8e0e_55.png)

![](img/edcedfaec63b0ada78f68ded050f8e0e_57.png)

以下是ACID属性的含义：
*   **原子性 (Atomicity)**：事务中的所有操作要么全部完成，要么全部不执行。
*   **一致性 (Consistency)**：事务将数据库从一个一致状态转变为另一个一致状态。
*   **隔离性 (Isolation)**：数据库系统给用户一种错觉，仿佛他们是系统的唯一用户，从而简化了并发编程。
*   **持久性 (Durability)**：一旦事务成功提交，其所做的更改将永久保存，不会因任何故障而丢失。

![](img/edcedfaec63b0ada78f68ded050f8e0e_59.png)

![](img/edcedfaec63b0ada78f68ded050f8e0e_61.png)

![](img/edcedfaec63b0ada78f68ded050f8e0e_63.png)

![](img/edcedfaec63b0ada78f68ded050f8e0e_65.png)

## 恢复机制

![](img/edcedfaec63b0ada78f68ded050f8e0e_67.png)

恢复机制与事务概念紧密相连，因为它必须处理任意时间点的崩溃。这意味着：
1.  数据库结构本身必须在崩溃后保持完好。
2.  即使在崩溃后，也必须维护事务的保证（特别是原子性和持久性）。

![](img/edcedfaec63b0ada78f68ded050f8e0e_69.png)

![](img/edcedfaec63b0ada78f68ded050f8e0e_71.png)

![](img/edcedfaec63b0ada78f68ded050f8e0e_72.png)

![](img/edcedfaec63b0ada78f68ded050f8e0e_74.png)

从技术层面看，事务和恢复通常分为两个部分：
*   **并发控制**：主要负责提供隔离性(I)和一致性(C)。
*   **日志记录**：主要负责提供原子性(A)和持久性(D)。

![](img/edcedfaec63b0ada78f68ded050f8e0e_76.png)

## 并发执行的挑战

![](img/edcedfaec63b0ada78f68ded050f8e0e_78.png)

![](img/edcedfaec63b0ada78f68ded050f8e0e_80.png)

![](img/edcedfaec63b0ada78f68ded050f8e0e_82.png)

我们希望数据库能被多个用户同时使用，以提高性能。然而，并发执行在带来性能好处的同时，也可能引发正确性问题。

以下是几种典型的并发问题：

![](img/edcedfaec63b0ada78f68ded050f8e0e_84.png)

![](img/edcedfaec63b0ada78f68ded050f8e0e_86.png)

![](img/edcedfaec63b0ada78f68ded050f8e0e_88.png)

*   **丢失更新**：两个事务读取同一数据项并分别更新，后一个更新会覆盖前一个，导致前一个更新丢失。
*   **脏读**：一个事务读取了另一个未提交事务写入的数据，而后该未提交事务被回滚，导致第一个事务读到了“从未存在”的数据。
*   **不可重复读**：一个事务两次读取同一数据项，但在两次读取之间，另一个事务修改并提交了该数据，导致第一个事务两次读取的结果不一致。
*   **幻读**：一个事务执行一个返回结果集的查询（例如 `SELECT * FROM R`），然后另一个事务插入新的元组并提交。当第一个事务再次执行相同查询时，会看到新的“幻影”元组。

![](img/edcedfaec63b0ada78f68ded050f8e0e_90.png)

![](img/edcedfaec63b0ada78f68ded050f8e0e_92.png)

![](img/edcedfaec63b0ada78f68ded050f8e0e_94.png)

## 可串行化

![](img/edcedfaec63b0ada78f68ded050f8e0e_96.png)

![](img/edcedfaec63b0ada78f68ded050f8e0e_98.png)

上述所有问题在事务串行执行（即一个接一个地执行）时都不会发生。但我们不希望串行执行，因为性能低下。因此，我们的目标是让并发执行的事务**表现得好像**是串行执行的一样。这个概念称为**可串行化**。

![](img/edcedfaec63b0ada78f68ded050f8e0e_100.png)

为了实现可串行化，我们需要进行一些簿记工作。具体的实现机制（如锁、时间戳排序等）将在后续课程中详细讨论。

![](img/edcedfaec63b0ada78f68ded050f8e0e_102.png)

本节课中我们一起学习了事务的基本概念、ACID属性、恢复机制的必要性，以及并发执行可能带来的问题。理解这些是掌握数据库系统实现中事务处理与恢复模块的基础。在接下来的课程中，我们将深入探讨这些机制的具体实现。