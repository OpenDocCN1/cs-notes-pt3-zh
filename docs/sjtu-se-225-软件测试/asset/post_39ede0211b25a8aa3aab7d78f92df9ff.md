
The large number of execution paths comes from nested loops. Condensation graphs eliminate loops (or at least condense them down to a single node); therefore, we can use this as a strategy to simplify situations that otherwise are computationally untenable.

- Program Graphs (omit)

## 2.7 Finite State Machines

有限（穷）状态机是形式化描述的有效方法，在计算机调度、管理中得到了广泛的应用。

我们通过一个简单的例子来说明有穷状态机的基本概念。

司机驾驶汽车，有以下状态。打开车门；车挡在启动档，插钥匙，打火发动汽车；挂前进档，汽车前行；挂后退档，汽车后退；挂启动档，熄火，拔钥匙；下车关门。

当然，油门和刹车也是两个重要的动作，一个是为了提速，一个是为了减速，但它们都不影响汽车的状态，这里予以简化。空档是一个过渡状态，为了简洁，也予以简化。

![](img/8454895dcf92bedbe5b40d0487077d64_95_0.png)

状态转换图在实际设计中往往被状态转换表所代替，下表是汽车驾驶的状态转换表。

| 当前状态/执行动作 | 准备状态 | 启动状态 | 前进状态 | 后退状态 |
|---|---|---|---|---|
| （挂启动档）打火 | 启动状态 | 启动状态 | 无效 | 无效 |
| 挂前进档 | 准备状态 | 前进状态 | ／ | 前进状态 |
| 挂后退档 | 准备状态 | 后退状态 | 后退状态 | ／ |
| 挂启动档 | 准备状态 | 启动状态 | 启动状态 | 启动状态 |
| 熄火 | 准备状态 | 准备状态 | 准备状态 | 准备状态 |

汽车驾驶的状态转换表

从上面的例子我们可以看到，一个有穷状态机包括以下5个部分：状态集J、输入（动作）集K、状态转换函数（转换表）T、初始态S和终止态F。对于上面的例子有穷状态机的各个部分如下：

- ◆ 状态集J：{准备状态，启动状态，前进状态，后退状态};
- ◆ 输入集K：{打火，熄火，挂前进档，挂后退档，挂启动档};
- ◆ 转换函数T：如表13-1所示;
- ◆ 初始态S：{准备状态};
- ◆ 终止态F：{准备状态};

由上面的说明，我们可以将有穷状态机表示为一个5元组（J, K, T, S, F），其中：

- J 是一个有穷的非空状态集；
- K 是一个有穷的非空输入集；
- T 是一个从（J-F）×K到J的转换函数；
- S ∈ J，是唯一的初始态；
- F J，是若干个终止态。

有穷状态机在计算机系统中应用的十分广泛。如操作系统中的作业调度与管理，GUI图形用户界面的驱动等。

## 2.8 Petri Net 说明

- Petri Net 的介绍与第11讲 交互测试密切关联，因此放在第11讲介绍。

## 2.9 State Charts

the StateChart notation: to devise a visual notation that combined the ability of Venn diagrams to express hierarchy and the ability of directed graphs to express connectedness (Harel, 1988).

If a state contains substates, as state A does, the edge “refers” to all substates.

Thus, the edge from A to D means that the transition can occur either from state B or from state C.

![](img/8454895dcf92bedbe5b40d0487077d64_100_0.png)

![](img/8454895dcf92bedbe5b40d0487077d64_100_1.png)

## 其它

对于软件测试而言，并不是仅仅需要本节介绍的数学知识。

形式化描述、数学验证、数据结构与算法等都是可能用到的数学。

在本课程中，将以软件测试的实践为主，不再过多介绍数学的知识。

## Q&A

## Chapter 3

## Fundamental theory and
methods of software test

- 3.1 Non-execution based Verification
- 3.2 Execution based Verification
- 3.3 Formal verification
- 3.4 Other methods

## 3.1 Non-execution based Verification

Not execute the program, tester could use some tools to review and analyze the specification and program code.

- walk through
- Inspection

### 3.1.1 Walk through

- Consist a walk through test group
- Check program code logic
- Generate test case, include input data and expect result.
- Put the data into program code, if the calculate result unequal the expect result, find an error.
- Check the code line by line.

a member of the SQA

one or more representative of implementation

a representative of next step

a client representative

![](img/8454895dcf92bedbe5b40d0487077d64_108_0.png)

![](img/8454895dcf92bedbe5b40d0487077d64_108_1.png)

![](img/8454895dcf92bedbe5b40d0487077d64_108_2.png)

![](img/8454895dcf92bedbe5b40d0487077d64_108_3.png)

The walkthrough team should consist of **four to six** individuals

- The goal of the walkthrough team is to detect faults, not to correct them.
- The person leading the walkthrough guides the other members of the team through the code.
- The walkthrough can be driven by the lists of issues compiled by team members or by the code itself, with team members raising their concerns at the appropriate time.
- In both cases, each issue will be discussed as it comes up and resolved into either a fault that needs to be addressed or a point of confusion that will be cleared up in the discussion

### 3.1.2 Inspection

- An inspection is a far more formal activity than a code walkthrough.
- It is conducted by a team of three to six people

a moderator

a representative of next step

one or more representative of implementation

a recorder
