

## § 6. 调试

### 1、调试技术

#### ① 输出存储器内容 (memory dump)

以八进制或十六进制的形式印出存储器的内容。

**缺点：**

- 输出信息量极大，不易解读且大多无用；
- 输出的是程序在某一时刻的静态情况，且往往不是出错时的状态。

#### ② 插入 “watch points” (或称 “spy points”)

- 人工插入打印缺点：
  - 改动源代码，增加了出错机会；
  - 打印信息可能太多。
- 自动调试工具 —— 无须打印额外信息，且不改动源代码

### 2、调试策略

调试过程的关键不是调试技术，而是用来推断错误原因的基本策略。主要有：

- ① 试探法，凭经验猜测。
- ② 回溯法：由症状 (symptom) 最先出现的地方，沿 control flow 向回检查。适用于小型程序。
- ③ 对分法：在关键点插入变量的正确值，则：

#### ④ 归纳法

从错误症状中找出规律，推断根源。

例：学生考试评卷报告。要求输出成绩排名、平均分、试题分析报告。

发现错误：对 51 个学生评分 → 中间值为 26（期望值 80）；对 1 个学生评分 → 中间值为 1。

| | Yes | No |
|---|---|---|
| **What** | 第 2 号报告中打印的中间值有误 | 平均值和标准偏差的计算 |
| **Where** | 在第 2 号报告中 | 在其它报告中，学生分数计算似乎正确 |
| **When** | 在对 51 个和 1 个学生评分的测试时发现 | |
| **How** | 51 个学生 → 中间值 = 26<br>1 个学生 → 中间值 = 1 | 对 2 个和 200 个学生计算时并无错误 |

观察分析：取奇数时出错？打印的是中间学生的编号而非分数？加测试来验证上述推测。

#### ⑤ 演绎法

普通 → 特殊。从假设中逐步排除、精化，从而导出错误根源。

## § 7. 软件可靠性 (Reliability)

### 1、基本概念

- 可靠性 (Reliability)：程序在给定的时间间隔内，按照说明书的规定，成功地运行的概率。
- 可用性 (Usability)：程序在给定的时间点，按照说明书的规定，成功地运行的概率。
- 正确性 (Correctness)：程序的功能正确。

设系统故障停机时间为 $t_{d1}, t_{d2}, \ldots$；正常运行时间为 $t_{u1}, t_{u2}, \ldots$；则系统的“稳态可用性”为

$$\text{Availability}=\frac{\text{MTTF}}{\text{MTTF}+\text{MTTR}}\qquad\text{(Shooman, 1983)}$$

其中 $\text{MTTF}=\text{Mean Time To Failure}=\frac{1}{n}\sum_{i=1}^{n}t_{ui}$

$\text{MTTR}=\text{Mean Time To Repair}=\frac{1}{n}\sum_{i=1}^{n}t_{di}$

### 换个角度看问题

$$E_c(\tau) = E_T - \frac{I_T}{K \cdot MTTF}$$

意义：可根据对软件平稳运行时间的要求，估算需改正多少个错误后才能结束测试。

还有一个问题 —— $E_T = ?$

估算方法：

① 植入故障法：

人为植入 $N_s$ 个故障，测后发现 $n_s$ 个植入故障和 $n$ 个原有故障，则设

$$\frac{n_s}{N_s} = \frac{n}{\hat{N}} \Rightarrow \hat{N} = \frac{n}{n_s} \approx E_T$$

② Hyman 分别测试法：

二人（组）分别独立测试同一程序，甲测得故障总数为 $B_1$，乙测得为 $B_2$，其中有 $b_c$ 是相同的，设以甲的测试结果为基准（即相当于①中的植入故障），则设

$$\frac{b_c}{B_1}=\frac{B_2}{\hat{B}}\Rightarrow \hat{B}=\frac{B_2}{b_c}B_1\approx E_T$$

一般多测几个 $\hat{B}$ 取平均。

### 3、正确性说明

目标：研究能证明程序正确性的自动系统。

**原理：**

a(i)：断言 (assertion)。证明：对任一个 i，执行了 $p_i$ 到 $p_{i+1}$ 之间的语句后，可将 a(i) 变为 a(i+1)，则证明由 a(1) 可导出 a(n)。若 a(1) 和 a(n) 正确，且程序确定可终止，则证明程序正确。

但是：即使有了正确性证明程序，软件测试也仍然是需要的。

因为：① 正确性证明只证明程序功能正确，但不能验证动态特性；② 证明过程本身也可能发生错误。

## § 8. 日立预测法

日立预测法——测试时间绘制并检查两种曲线。

### 1、测试完成率曲线：

> 经验：工程的成败取决于第一阶段向第二阶段转移断点的位置，一般成功的工程其转折点位于 15%；若超过 55% 则破产不可避免。

### 2、错误发现率曲线：

错误发现率 = 单位时间内发现的错误数。

> **经验：** 刚过峰值点后曲线的导数关系到工程的成败。若导数值大于 0.3，则失败不可避免。

其它可靠性预测模型 (reliability prediction model)：

- 最早：Jelinski - Moranda model (1972)
- 最广泛应用：Musa model (1990)
- 最近：Fenton - Pfleeger model (1997)

## § 9. 自动测试工具

### 1、测试数据生成程序 (Test case generator)

功能：自动生成大量输入数据。

**主要用于：**

- 测试系统在实际环境中的性能（例如测试数据库管理系统）；
- 自动校核系统输出（若输出数据的语法可以被形式地说明）。

缺点：不能自动生成预期的输出，因此用途有限。

### 2、动态分析程序 (Dynamic analyzer)

功能：分析程序中每个语句的执行次数。

**组成：**

- 检测部分：插入检测语句，负责收集、整理语句执行次数；
- 显示部分：以容易理解的形式印出收集的信息。

**用途：**

- 发现测试中没有执行的语句，以增加相应的测试用例；
- 发现不按要求终结的循环；
- 发现不应执行却执行了的代码，及应执行而未执行的代码。

### 3、静态分析程序 (Static analyzer)

不执行程序，仅扫描程序的正文，从中寻找可能导致错误的异常情况。

### 4、文件比较程序 (File inspector)

主要步骤：

1. 建立一个文件存放预期的正确结果；
2. 执行测试，将输出数据存进另一个文件；
3. 使用文件比较程序来比较上述两个文件，印出两者之差异。

作业：P.164 # 7

## 第八章 维护 (Maintenance) —— 亦称 Software Evolution

### § 1. 定义

#### 例：成功的维护

In 1993, Bell Atlantic introduced the **SaleService Negotiation System** (SSNS) to replace three legacy systems that supported operators taking orders for new telephone-based services. The **initial goals** of the system were to **minimize errors** and to **reduce the amount of time** customer service representatives spend on the telephone with customers. But as the sales representatives used the system, management realized the system’s **great potential to provides on-screen cues** reminding representatives of Bell Atlantic products that might meet the customers’ needs. The goals of the system changed, **from order-taking to needs-based sales**.

