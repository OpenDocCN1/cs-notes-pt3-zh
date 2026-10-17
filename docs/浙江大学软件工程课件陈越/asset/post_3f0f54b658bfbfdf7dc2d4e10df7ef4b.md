

# § 4. 系统分解

## ② 设计策略

- 将用户分类（按技能、职务等）
- 描述用户的类型、水平、使用目的、其它特征（如年龄、性别、习惯等），写出操作脚本
- 设计命令层次：注意同用户熟悉的方式（如 Windows 界面）尽量保持一致。次序、深度、宽度调整适当
- 设计 HCI 类：例如 VC 提供的 MFC 类库（Microsoft Foundation Class Library）

## (3) 任务管理子系统：基于 OOA 建立的 dynamic model

### ① 分析并发性：

- 若两个 objects 之间无交互行为，或它们同时接受 events，则它们本质上是并发的 (synchronous)
- 考察 event flow diagram，找出没有并发对象的路径（称为控制线），每条对应一个任务 (task，亦称 process)
- 不同的 tasks 对应必须同时发生的不同行为

### ② 确定 task 类型，并分配给适当的软件硬件去执行

- **事件驱动型 (event-driven)**：主要完成通信工作。
  - event = 数据到达的 interrupt
- **时钟驱动型 (clock-driven)**：完成周期性工作。
- **优先型 (priority)**：将 high priority 或 low priority 的任务专门分离出来先做或后做。
- **关键任务 (key task)**：指关系系统成败的处理，要求高可靠性，应分离考虑，严格测试。
- **协调任务 (coordinator)**：当系统中存在三个以上 tasks 时，应增设一个协调任务，用于封装不同 tasks 之间的协调控制。

## (4) 数据管理子系统：

### ① 选择管理模式

- 文件管理 (file manager) 系统
- 关系数据库 (Relational Data Base) 管理系统
- 面向对象数据库 (OODB) 管理系统

### ② 设计数据格式及相应的服务

（请参阅教材 p.252 - 255）

# § 5. 设计类中的服务
——细化 object model 中的 methods

## 1、确立服务

### （1）从 dynamic model 出发：Event flow diagram 中

- Event = message；
- 接受 message 的 object 必有对应的 method；
- Method 改变 status（即 attributes），并完成 action。

# § 5. 设计类中的服务

**注意：** Action（即算法）与 status 有关。例如：不同 status 接受同一个 event 时，其 action 不同——

![](img/caa6e55d367968a29a6a558fa69d0413_307_0.png)

则算法应有 DO_CASE 型控制

### （2）从 function model 出发：

DFD 的一般结构是

![](img/caa6e55d367968a29a6a558fa69d0413_307_1.png)

# § 5. 设计类中的服务

若 Process=从 Input Flow 中抽取一个值，则

若 I 和 O 类型相同，而 output 实质上是 input 的另一个状态，则 I\O 是一类，有

若

则

| Input Flow Class |
|------------------|
| ......           |
| Process          |

| I\O Class |
|-----------|
| ......    |
| Process   |

| Output Flow Class |
|-------------------|
| ......            |
| Process           |

![](img/caa6e55d367968a29a6a558fa69d0413_308_0.png)

# § 5. 设计类中的服务

若 Process Storage 则 Storage Class ...... Process

对照 DFD 与 Class-&-Object 图，若一个 process 涉及多个 classes，则必须判断它属于哪一个 class。

例如：Activator Process Receiver 若 Process 改变了 Receiver，则 Receiver Class ...... Process

又如：从关联上看，process 所涉及的所有 classes 中，处于中心地位的 class，一般拥有该 process。

# ## 2、设计实现方法

### (1) 算法设计：要求做到易修改，并且复杂度低（即效率高）易理解，易实现。

![](img/caa6e55d367968a29a6a558fa69d0413_310_0.png)

### (2) 数据结构设计：需要考虑具体的物理结构的选择。

### (3) 新添用于存放内部处理中间结果的 class；引入新的低层操作，进一步细化。

# § 6. 设计关联

## 方法2：设公司的属性雇员为一指针集。（快速）

![](img/caa6e55d367968a29a6a558fa69d0413_312_0.png)

## 2、双向关联

### 方法1：将上述两种单向关联结合使用

![](img/caa6e55d367968a29a6a558fa69d0413_312_1.png)

### 方法2：另设关联类（特别适用于链属性）

![](img/caa6e55d367968a29a6a558fa69d0413_312_2.png)

# § 7. 优化

## 1、确定优先级：

必须站在全局高度确定各项质量指标的优先级，在优化设计时制定折衷方案。切忌各子系统自以为是，导致最终优化目标对立。

最常见的情况是在效率与清晰性之间的折衷。

## 2、提高效率的技术

### ① 增加关联（类）

例：设某公司有 2000 名雇员，平均每名雇员会 10 种技能，其中有 5 人精通日语，现要查询公司中会讲日语的雇员是哪些人

![](img/caa6e55d367968a29a6a558fa69d0413_313_0.png)

# § 7. 优化

1. **方法1：** 嵌套查询——遍历雇员 2000 次，而对每个雇员遍历技能 10 次。命中率为 1/4000。
2. **方法2：** 用 Hash Table 实现技能，使“会讲日语”对应唯一的技能对象，则命中率上升为 1/400。
3. **方法3：** 增加一个额外的限定关联“精通语言”，即可立刻查得结果。

![](img/caa6e55d367968a29a6a558fa69d0413_314_0.png)

建立这样的索引必然多占空间，而且基关联改变时也必须相应地修改索引。因此，应只给那些经常执行并且开销大、命中率低的查询建立索引。

### ② 调整查询次序，优化算法

例如公司有 5 名会日语的雇员，有 200 名会法语的雇员。现要找日、法语均会的雇员，则应先找会日语雇员，再从中找会法语的雇员。

### ③ 保留内部中间过程中产生的派生属性。

## 3、调整继承关系

### ① 向上归纳

### ② 向下派生

### ③ 利用委托 (commitment)

例：实现 Stack 方法1：从 List 派生 push = last + add pop = last + remove 问题：Stack.first 也是合法的。

方法2：把 List 作为 Stack 的一个 attribute，称为 commitment。这种方法比较安全 (Stack.first 为非法)。

作业：自习第十二章 OOP，并回答问题 P.275 #3, #5。

![](img/caa6e55d367968a29a6a558fa69d0413_316_0.png)

![](img/caa6e55d367968a29a6a558fa69d0413_316_1.png)

§ 7. 优化

# Project Part VI
HDIS 期末合并版首次面世

- 验收截止日期：1月16日
- 验收地点：各组自定
- 验收内容：
  - 数据库合并情况；
  - 用户界面合并情况。

# 第十三章 管理技术 (Software Management)

![](img/caa6e55d367968a29a6a558fa69d0413_318_0.png)

![](img/caa6e55d367968a29a6a558fa69d0413_318_1.png)

![](img/caa6e55d367968a29a6a558fa69d0413_318_2.png)

![](img/caa6e55d367968a29a6a558fa69d0413_318_3.png)

![](img/caa6e55d367968a29a6a558fa69d0413_318_4.png)

![](img/caa6e55d367968a29a6a558fa69d0413_318_5.png)

