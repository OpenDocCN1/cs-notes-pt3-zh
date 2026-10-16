

## 平板与拆分

aaa.com

cnn.com

cnn.com/sports.html

TABLETS

Website.com

...

Yahoo.com/kids.html

Yahoo.com/kids.html?D

...

Zuppa.com/menu.html

“语言”

“内容”

EN

“<html>…”

## 服务器

- 平板服务器管理平板，每个服务器多个平板。每个平板为 100-200 兆
  - 每个平板仅存在于一个服务器上
  - 平板服务器拆分过大平板

- 主服务器负责负载均衡和容错
  - 使用 Chubby 监控平板服务器健康状况，重启失败服务器
  - GFS 复制数据。优先在数据已存在机器上启动平板服务器

![](img/ef3eda0c8c755c94cf60f8794999a1a7_205_0.png)

![](img/ef3eda0c8c755c94cf60f8794999a1a7_205_1.png)

![](img/ef3eda0c8c755c94cf60f8794999a1a7_205_2.png)

## 典型集群

Cluster Scheduling Master

Lock Service

GFS Master

Machine 1

Machine 2

Machine 3

![](img/ef3eda0c8c755c94cf60f8794999a1a7_207_0.png)

![](img/ef3eda0c8c755c94cf60f8794999a1a7_207_1.png)

![](img/ef3eda0c8c755c94cf60f8794999a1a7_207_2.png)

## Google 应用

| Project name | Table size (TB) | Compression ratio | # Cells (billions) | # Column Families | # Locality Groups | % in memory | Latency-sensitive? |
|---|---|---|---|---|---|---|---|
| Crawl | 800 | 11% | 1000 | 16 | 8 | 0% | No |
| Crawl | 50 | 33% | 200 | 2 | 2 | 0% | No |
| Google Analytics | 20 | 29% | 10 | 1 | 1 | 0% | Yes |
| Google Analytics | 200 | 14% | 80 | 1 | 1 | 0% | Yes |
| Google Base | 2 | 31% | 10 | 29 | 3 | 15% | Yes |
| Google Earth | 0.5 | 64% | 8 | 7 | 2 | 33% | Yes |
| Google Earth | 70 | – | 9 | 8 | 3 | 0% | No |
| Orkut | 9 | – | 0.9 | 8 | 5 | 1% | Yes |
| Personalized Search | 4 | 47% | 6 | 93 | 11 | 5% | Yes |

## 数据库技术与应用

![](img/ef3eda0c8c755c94cf60f8794999a1a7_209_0.png)

北京邮电大学计算机学院 肖达

xiaoda99@gmail.com

## 关系数据库简介

- 1962年CODASYL发表“信息代数”
- 1968年David Child在IBM 7090机上实现的集合论数据结构

- 系统地、严格地提出关系模型的是美国IBM公司的 **E. F. Codd**
  - 1970年提出关系数据模型

    > E.F.Codd, “A Relational Model of Data for Large Shared Data Banks”, Communication of the ACM, 1970

  - 之后，提出了关系代数和关系演算的概念
  - 1972年提出了关系的第一、第二、第三范式
  - 1974年提出了关系的BC范式

- Codd生平
  - 牛津大学主攻数学，毕业后进入IBM，主持多道程序设计系统和流水线计算机研制。
  - 年近40岁重返大学，42岁获得博士学位，47岁发表关系数据库论文，58岁获得图灵奖。

## 第二章 关系数据库

- **2.1 关系数据结构及形式化定义**
- **2.2 关系操作**
- **2.3 关系代数**
- **2.4 关系的完整性**

### 2.1 关系数据结构及形式化定义

- 2.1.1 关系
- 2.1.2 关系模式
- 2.1.3 关系数据库

### 2.1.1 关系

- 单一的数据结构—关系

  现实世界的实体以及实体间的各种联系均用关系来表示

- 逻辑结构—二维表

  从用户角度，关系模型中数据的逻辑结构是一张二维表

- 建立在集合代数的基础上

### 关系 (续)

1. 域（Domain）
2. 笛卡尔积（Cartesian Product）
3. 关系（Relation）

### 1. 域（Domain）

域是一组具有相同数据类型的值的集合。例：

- 整数
- 实数
- 介于某个取值范围的整数
- 指定长度的字符串集合
- {'男'， '女'}
- ……

### 2. 笛卡尔积（Cartesian Product）

- 笛卡尔积

给定一组域 D₁，D₂，…，Dₙ，这些域中可以有相同的。

D₁，D₂，…，Dₙ 的笛卡尔积为：

D₁ × D₂ × … × Dₙ =

{ (d₁, d₂, …, dₙ) | dᵢ ∈ Dᵢ, i = 1, 2, …, n }

- 所有域的所有取值的一个组合

- 不能重复

### 笛卡尔积（续）

- **元组（Tuple）**
  - 笛卡尔积中每一个元素 `(d₁, d₂, ⋯, dₙ)` 叫作一个 n 元组（n-tuple）或简称元组（Tuple）
  - （张清玫，计算机专业，李勇）、（张清玫，计算机专业，刘晨）等都是元组

- **分量（Component）**
  - 笛卡尔积元素 `(d₁, d₂, ⋯, dₙ)` 中的每一个值 `dᵢ` 叫作一个分量
  - 张清玫、计算机专业、李勇、刘晨等都是分量

- **基数（Cardinal number）**
  - 若 `Dᵢ (i=1, 2, ⋯, n)` 为有限集，其基数为 `mᵢ (i=1, 2, ⋯, n)`，则 `D₁×D₂×⋯×Dₙ` 的基数 `M` 为：

    `M = ∏ⁿᵢ₌₁ mᵢ`

- **笛卡尔积的表示方法**
  - 笛卡尔积可表示为一个二维表
  - 表中的每行对应一个元组，表中的每列对应一个域

### 笛卡尔积（续）

例：设

D₁为教师集合（T）={t₁, t₂}

D₂为学生集合（S）={s₁, s₂, s₃}

D₃为课程集合（C）={c₁, c₂}

则D₁×D₂×D₃是个三元组集合，元组个数为2×3×2，是所有可能的（教师，学生，课程）元组集合

| T | S | C |
|---|---|---|
| t₁ | s₁ | c₁ |
| t₁ | s₁ | c₂ |
| t₁ | s₂ | c₁ |
| ... | ... | ... |
| t₂ | s₃ | c₂ |

**表 2.1 D₁， D₂， D₃ 的笛卡尔积**

| SUPERVISOR | SPECIALITY | POSTGRADUATE |
|---|---|---|
| 张清玫 | 计算机专业 | 李勇 |
| 张清玫 | 计算机专业 | 刘晨 |
| 张清玫 | 计算机专业 | 王敏 |
| 张清玫 | 信息专业 | 李勇 |
| 张清玫 | 信息专业 | 刘晨 |
| 张清玫 | 信息专业 | 王敏 |
| 刘逸 | 计算机专业 | 李勇 |
| 刘逸 | 计算机专业 | 刘晨 |
| 刘逸 | 计算机专业 | 王敏 |
| 刘逸 | 信息专业 | 李勇 |
| 刘逸 | 信息专业 | 刘晨 |
| 刘逸 | 信息专业 | 王敏 |

