# 003：ParadeDB – 专为搜索与分析打造的Postgres

![](img/b36d9a9e65622aa80282e164288f1607_1.png)

在本节课中，我们将学习ParadeDB如何通过集成数据库构建块来增强PostgreSQL，使其成为一个强大的全文搜索和分析引擎。我们将探讨PostgreSQL现有全文搜索功能的局限性，并深入了解ParadeDB如何利用Rust库Tantivy和自定义PostgreSQL扩展API来解决这些问题，特别是围绕BM25评分、复杂查询和快速聚合（分面搜索）等方面。

---

## 现有PostgreSQL全文搜索功能

在深入了解ParadeDB的改进之前，让我们先回顾一下PostgreSQL内置的全文搜索功能。这有助于我们理解其局限性以及改进的空间。

PostgreSQL提供了三种主要的全文搜索方法。

### LIKE操作符

`LIKE`操作符是一种基础的字符串匹配方式。其语法如下：
```sql
SELECT * FROM users WHERE name LIKE 'John%';
```
此查询将匹配所有以“John”开头的名字。然而，`LIKE`操作符速度较慢，并且缺乏对搜索结果进行相关性排序的概念，所有匹配项都被平等对待。

### TSVECTOR与TS_RANK

PostgreSQL的核心全文搜索功能使用`tsvector`数据类型和`ts_rank`函数。`tsvector`存储文本的标记化（分词）和词干提取后的表示形式。`ts_rank`函数在底层实现了**TF-IDF（词频-逆文档频率）**算法。

**TF-IDF公式**的核心思想是：一个词在单个文档中出现越频繁（词频高），且在整个文档集合中出现越少（逆文档频率高），则该词对该文档的相关性贡献越大。

为了加速搜索，可以在`tsvector`列上创建GIN（通用倒排索引）索引，以避免全表扫描。

### PG_TRGM扩展

`pg_trgm`是PostgreSQL的一个核心扩展，它将单词分割成三个字符的组（三元组）。例如，单词“cheeses”的三元组是：`che`, `hee`, `ees`, `ses`。它可以用于实现基本的模糊匹配或自动补全功能，但功能相对有限。

---

## PostgreSQL全文搜索的不足

上一节我们介绍了PostgreSQL现有的搜索工具，本节我们来看看它存在哪些主要不足，这正是ParadeDB致力于解决的问题。

PostgreSQL的全文搜索在以下几个方面有所欠缺：

1.  **BM25相关性评分**：PostgreSQL使用TF-IDF进行排名。**BM25**是一种更先进的排名算法，它改进了TF-IDF，考虑了文档长度和词频饱和度，能产生更符合用户期望的相关性排序。
2.  **强大的分词与过滤器**：对非拉丁语系（如中文）的支持不佳，缺乏多语言混合查询等高级分词能力。
3.  **类Elasticsearch的复杂查询API（DSL）**：难以构建复杂的搜索逻辑，例如对不同词项进行加权、布尔组合等。
4.  **快速的分面搜索与聚合**：在数百万行数据上执行`COUNT(*)`等聚合操作非常缓慢，而这在搜索结果的统计分析中非常常见。

---

## ParadeDB的解决方案：PG_SEARCH

ParadeDB的核心是一个名为PG_SEARCH的PostgreSQL扩展，它通过集成Rust搜索库**Tantivy**来解决上述问题。Tantivy是一个受Apache Lucene启发的库，以其速度和功能集而闻名。

以下是ParadeDB实现其目标的四个关键技术：

### 1. 自定义全文搜索操作符

ParadeDB引入了`@@`操作符（灵感来自PostgreSQL的`tsvector`操作符），允许在标准SQL查询中嵌入全文搜索。例如：
```sql
SELECT * FROM mock_items WHERE id < 10 AND description @@ 'keyboard';
```
这个操作符将搜索词“keyboard”传递给底层的Tantivy引擎执行搜索，并且可以与其他SQL谓词（如`id < 10`）无缝结合。

### 2. BM25倒排索引

为了加速查询，ParadeDB创建了一种新的索引类型——**BM25索引**。它使用PostgreSQL的索引访问方法API，将Tantivy的倒排索引功能集成进来。

这个索引的一个关键特性是它是一个**覆盖索引**，可以创建在多个列上。这使得ParadeDB能够将多个搜索谓词和排序操作下推到索引层一次性完成，极大地提升了性能。

### 3. 查询构建器API

为了支持复杂的搜索逻辑，ParadeDB提供了查询构建器API。它通过用户定义函数（UDF）抽象了底层的JSON查询语法，让用户能以更“PostgreSQL风格”的方式编写查询。例如，实现词项加权（boosting）：
```sql
-- 搜索“running shoes”，但使“shoes”的权重是“running”的两倍
SELECT * FROM mock_items WHERE description @@ websearch_to_tsquery('running shoes', boost => ARRAY['shoes:2.0']);
```

### 4. 自定义扫描（Custom Scan）

这是ParadeDB最强大的部分，它利用PostgreSQL的Custom Scan API深度优化查询执行。它主要实现了三个功能：

*   **谓词下推**：将`WHERE`子句中的多个条件（只要它们在BM25索引中）合并，并下推到Tantivy执行单次索引扫描。
*   **BM25评分投影**：将BM25相关性分数作为一个新的列直接返回给用户，无需额外调用UDF计算。
*   **快速分面与聚合（进行中）**：这是当前的重点工作。目标是利用Tantivy的**快速字段**（一种列式存储格式）和**DataFusion**（一个用Rust编写的嵌入式查询引擎）来加速聚合查询（如`COUNT`, `SUM`）。

---

## 挑战：MVCC与列式聚合

上一节我们提到了利用DataFusion加速聚合的愿景，本节我们来探讨实现这一目标所面临的核心挑战：**多版本并发控制（MVCC）**。

PostgreSQL使用MVCC来保证事务的隔离性。简单来说，它通过事务ID和快照来决定某一行数据对当前事务是否“可见”。

当ParadeDB试图将聚合计算下推到由Tantivy存储、由DataFusion处理的列式数据时，就遇到了MVCC合规性问题。DataFusion引擎本身并不感知PostgreSQL的MVCC规则。如果盲目地对列式索引进行`COUNT`，可能会包含或排除不应计数的行（例如，尚未提交的插入或删除），导致结果不准确。

目前，团队正在评估几种解决方案：

1.  **让DataFusion感知MVCC**：在DataFusion中实现PostgreSQL的可见性检查函数，使其能根据事务快照过滤行。这需要处理DataFusion的多线程执行与PostgreSQL单线程模型的协调。
2.  **在索引中重新实现MVCC**：通过PostgreSQL触发器，将事务ID（xmin, xmax）信息直接存储到ParadeDB的索引中。这样DataFusion在处理时就能自行判断可见性。但这会增加写操作的开销和索引的复杂性。
3.  **探索其他架构**：这是一个活跃的研究领域，也有其他项目（如Postgres Pro的VOPS、ZomboDB）进行过类似探索。

实现一个MVCC安全的快速分析引擎，是ParadeDB将全文搜索优势扩展到更广泛分析场景的关键一步。

---

## 总结

本节课中，我们一起学习了ParadeDB如何改造PostgreSQL，使其成为一个强大的搜索和分析数据库。

我们首先回顾了PostgreSQL原生全文搜索工具（`LIKE`、`tsvector`、`pg_trgm`）及其在**BM25评分**、**复杂查询**和**快速聚合**方面的不足。接着，我们深入探讨了ParadeDB的解决方案：通过**PG_SEARCH**扩展集成**Tantivy**搜索库，并利用PostgreSQL的扩展API实现了**自定义操作符**、**BM25索引**、**查询构建器**和强大的**自定义扫描**功能。最后，我们了解了当前在实现**快速列式聚合**（分面搜索）时，如何确保与PostgreSQL核心的**MVCC**事务模型兼容所面临的挑战和可能的解决思路。

![](img/b36d9a9e65622aa80282e164288f1607_3.png)

ParadeDB的探索展示了通过模块化方式，将专业的“数据库构建块”集成到成熟系统中，从而快速赋予其新能力的强大潜力。