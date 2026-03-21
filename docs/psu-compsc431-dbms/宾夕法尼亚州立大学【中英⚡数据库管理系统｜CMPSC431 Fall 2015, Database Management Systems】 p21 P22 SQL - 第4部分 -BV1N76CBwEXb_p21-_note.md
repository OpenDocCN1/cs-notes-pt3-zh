# 数据库管理系统：第4章：SQL - 第4部分

在本节课中，我们将要学习SQL查询中更高级的概念，包括嵌套查询的深入理解、分组聚合操作（GROUP BY和HAVING子句）以及它们之间的区别。我们将通过具体的查询实例来掌握这些核心技巧。

## 课程安排与作业更新

在开始新内容之前，我们先了解一下接下来的课程安排。本周我们将完成SQL部分的学习，并在周三开始介绍NoSQL数据库，具体会以MongoDB为例进行实践。请大家在课后可以自行搜索并安装MongoDB。

关于作业，作业三的截止日期是本周五。原定于下周五截止的作业四，由于NoSQL课程开始较晚，已顺延至两周后提交，该作业将完全围绕MongoDB展开。

下周，大家需要根据助教本周发出的邮件和日程表，预约时间进行项目演示。演示的详细要求已在项目描述中说明，如有疑问可以随时向我提问。

课程结束前，我们将进行一次简单的小测验。

![](img/9583a86de936c16329089eb0c22d62e7_1.png)

## 回顾：嵌套查询与关系除法

上一节我们介绍了嵌套查询，现在我们来深入理解一个容易混淆的查询——实现关系除法的概念。

这个查询的目标是：**找出预订了所有船只的船员姓名**。其SQL命令如下：
```sql
SELECT S.sname
FROM Sailors S
WHERE NOT EXISTS (
    SELECT B.bid
    FROM Boats B
    WHERE NOT EXISTS (
        SELECT R.bid
        FROM Reserves R
        WHERE R.bid = B.bid AND R.sid = S.sid
    )
);
```
这个三层嵌套查询的逻辑可以理解为：选择那些**不存在**任何一艘船（B）**没有被**该船员（S）预订过的船员。

为了更清晰地理解其执行过程，我们可以将其想象为三层循环：
1.  外层循环：遍历每个船员（Sailor S）。
2.  中层循环：对于当前船员，遍历每一艘船（Boat B）。
3.  内层循环：检查当前船员是否预订了当前这艘船。

内层`NOT EXISTS`子句检查“该船员没有预订这艘船”的情况是否为假。中层`NOT EXISTS`子句检查“存在一艘船该船员没有预订”的情况是否为假。最终，外层查询只选择那些“不存在任何一艘船他没有预订”的船员，即预订了所有船的船员。

## 新的查询模式：与子查询结果比较

本节我们来看看如何比较查询结果。考虑这个查询：**找出年龄大于等级为10的船员中最年长者的船员姓名**。

![](img/9583a86de936c16329089eb0c22d62e7_3.png)

解决思路分为两步：
1.  首先，找到等级为10的船员中的最大年龄。这是一个聚合查询。
    ```sql
    SELECT MAX(age) AS max_age
    FROM Sailors
    WHERE rating = 10;
    ```
2.  然后，在外层查询中，将此结果作为阈值进行比较。
    ```sql
    SELECT S.sname
    FROM Sailors S
    WHERE S.age > (SELECT MAX(age) FROM Sailors WHERE rating = 10);
    ```
    由于内层查询返回的是单个值（标量），因此可以直接在`WHERE`子句中使用比较运算符（`>`）。

另一种方法是使用`ALL`关键字，无需先求最大值：
```sql
SELECT S.sname
FROM Sailors S
WHERE S.age > ALL (SELECT age FROM Sailors WHERE rating = 10);
```
`ALL`表示外层查询的年龄需要大于子查询返回集合中的**每一个**值，这等价于大于其中的最大值。

在性能上，第一种方法（先求`MAX`）通常更优，因为外层查询的每一行只需要与一个标量值比较。而使用`ALL`时，每一行都需要与子查询结果集中的每一行进行比较。

## 引入分组聚合：GROUP BY 与 HAVING

到目前为止，我们学习的聚合函数（如`MAX`, `AVG`）都是针对整个结果集。现在，我们引入`GROUP BY`子句，它允许我们根据一个或多个列对结果集进行分组，然后在每个组内进行聚合计算。

`GROUP BY`的基本语法结构是：
```
SELECT ... FROM ... [WHERE ...] GROUP BY ... [HAVING ...]
```
*   `WHERE`：对**每一行**元组进行过滤。
*   `GROUP BY`：根据指定列对过滤后的行进行分组。
*   `HAVING`：对**每一个分组**进行过滤（分组资格）。
*   `SELECT`：选择要输出的列，对于使用了`GROUP BY`的查询，`SELECT`列表中的列通常只能是分组列或聚合函数表达式。

例如，查询**每个等级中最年轻船员的年龄**：
```sql
SELECT rating, MIN(age) AS min_age
FROM Sailors
GROUP BY rating;
```
这里，`rating`是分组列，`MIN(age)`是组内聚合计算。`AS min_age`用于为聚合结果列赋予一个易读的名称。

## 理解查询执行顺序与 HAVING 的用法

为了更好地编写分组查询，我们需要理解其概念上的执行顺序：
1.  **FROM**：计算`FROM`子句中表的笛卡尔积（本例只有一张表，可忽略）。
2.  **WHERE**：根据`WHERE`子句的条件，过滤掉不满足条件的行。
3.  **SELECT**（初步）：根据`SELECT`列表，丢弃不需要的列（但此时聚合尚未发生）。
4.  **GROUP BY**：将剩余的行按照`GROUP BY`指定的列进行分组。
5.  **HAVING**：将`HAVING`子句的条件应用于每个分组，淘汰不满足条件的分组。
6.  **SELECT**（最终）：为每个保留下来的分组生成一个输出元组，计算`SELECT`列表中的聚合函数和分组列。

让我们通过一个复杂点的例子来运用`WHERE`和`HAVING`：**找出每个至少拥有两名船员的等级中，年龄至少18岁的船员的最小年龄**。
```sql
SELECT rating, MIN(age)
FROM Sailors
WHERE age >= 18
GROUP BY rating
HAVING COUNT(*) >= 2;
```
*   `WHERE age >= 18`：首先过滤出行，只保留年龄≥18的船员。
*   `GROUP BY rating`：然后按等级分组。
*   `HAVING COUNT(*) >= 2`：最后，只保留那些分组内行数（即船员数）≥2的组。

## 分组查询实践：多表连接与常见错误

![](img/9583a86de936c16329089eb0c22d62e7_5.png)

现在我们将分组应用于多表查询。查询**每艘红色船只的预订次数**。
```sql
SELECT B.bid, COUNT(*) AS reservation_count
FROM Boats B, Reserves R
WHERE B.bid = R.bid AND B.color = 'red'
GROUP BY B.bid;
```
1.  `FROM ... WHERE`：连接`Boats`和`Reserves`表，并筛选出红色船只的预订记录。
2.  `GROUP BY B.bid`：按船只ID分组。**注意**，`SELECT`列表中的`B.bid`必须是分组列，这样才能正确显示每艘船。
3.  `COUNT(*)`：统计每个分组（即每艘船）中的记录数，即预订次数。

一个常见的错误是试图在`HAVING`子句中过滤行级条件：
```sql
-- 错误示例
SELECT B.bid, COUNT(*)
FROM Boats B, Reserves R
WHERE B.bid = R.bid
GROUP BY B.bid
HAVING B.color = 'red'; -- 错误！color不是分组列，且HAVING用于过滤组，而非行。
```
`HAVING B.color = 'red'`是不允许的，因为在分组后，每个组可能包含多行（尽管此例中按`bid`分组后`color`相同，但SQL语法上不允许引用非分组且非聚合的列）。过滤颜色必须在`WHERE`子句中进行。

## 综合练习：区分 WHERE 与 HAVING 的条件

考虑查询：**找出每个至少拥有两名船员的等级中，船员的平均年龄**。
```sql
SELECT rating, AVG(age)
FROM Sailors
GROUP BY rating
HAVING COUNT(sid) >= 2;
```
这里，`COUNT(sid) >= 2`是分组级别的条件，因此使用`HAVING`。

再看一个更复杂的：**找出每个至少拥有两名船员的等级中，年龄超过18岁的船员的平均年龄**。
```sql
SELECT rating, AVG(age)
FROM Sailors
WHERE age > 18
GROUP BY rating
HAVING 2 <= (SELECT COUNT(*) FROM Sailors S2 WHERE S2.rating = Sailors.rating);
```
*   `WHERE age > 18`：先过滤出年龄>18的船员。
*   `GROUP BY rating`：按等级分组。
*   `HAVING ...`：这里不能直接用`COUNT(sid) >= 2`，因为经过`WHERE`过滤后，`COUNT(sid)`只计算了年龄>18的船员。但题目要求“该等级至少有两名船员”（不限年龄）。因此，我们需要一个关联子查询来统计原表中该等级的总人数。

本节课中我们一起学习了SQL查询的进阶知识，包括复杂嵌套查询的逻辑剖析、使用`GROUP BY`进行数据分组聚合、以及利用`HAVING`子句对分组结果进行筛选。关键点在于清晰区分`WHERE`（行过滤）和`HAVING`（组过滤）的使用场景，并理解查询语句的执行顺序。掌握这些概念后，你就能编写出功能强大且高效的数据检索语句了。