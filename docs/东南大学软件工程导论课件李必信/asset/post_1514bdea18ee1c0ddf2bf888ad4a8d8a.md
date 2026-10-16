
## （A.3）软件工程理论体系形成

1968/1969，NATO

## 软件工程理论体系

指导

指导

### 软件开发实践
- 1. 软件工程概念
- 2. 软件开发方法
- 3. 软件过程
- 4. 软件模型
- 5. 编程语言
- 6. 开发环境与工具
- 7. ……

### 软件工程管理
- 1. 风险管理（risk）
- 2. 人员管理（people）
- 3. 项目管理（project）
- 4. 过程管理（process）
- 5. 产品管理（product）
- 6. 质量管理与控制
- 7. ……

## （B）第二次软件危机（1968 to 2001）

## （B.1）危机表现
- The project will produce the wrong product[有错的产品].
- The project will produce a product of inferior quality[低质量的产品].
- The project will be late[延迟].
- We’ll have to work 80 hour weeks[每周工作80小时].
- We’ll have to break commitments[违约].
- We won’t be having fun[没有休闲时间].

## （B.2）危机根源
- The assumption is that requirements can be fully understood prior to development
- Interaction with the customer occurs only at the beginning (requirements) and end (after delivery)
- Unfortunately the assumption almost never holds

![](img/fcdc64f47992afbcce2e20fafbbb0375_12_0.png)

## （B.3）软件工程理论体系完善
- Reduce risks by improving visibility—**white-box**
- Allow project **changes** as the project progresses
  - based on feedback from the customer

![](img/fcdc64f47992afbcce2e20fafbbb0375_13_0.png)

No silver bullet

## （C）第三次软件危机（2001 to present）
- （C.1）危机表现
  - 变更/演化/重用（质量、效率、成本）
  - 知识产权问题、安全问题
- （C.2）危机根源
  - 大量遗产系统的挖掘和重用
  - 大量开源软件/代码的使用
  - 普遍存在的动态/不确定需求
- （C.3）软件工程理论体系发展/重建
  - 自动化
  - 智能化/智慧化
    - 自适应、自测试、自修复、自主演化
  - 自主软件（混源软件、开源软件、闭源软件）

## （2）什么软件工程核心关注点

| 关注点 | 问题 | 手段 |
|---|---|---|
| 质量<br>效率<br>成本<br>变更<br>…… | 如何提高产品质量 | 软件质量保障技术 |
|  | 如何提高管理效率，降低成本，缩短上市时间 | 软件工程过程模型 |
|  | 如何提高开发效率，解决维护难的问题 | 软件开发方法/语言/工具 |
|  | 如何适应用户需求变更 | 演化维护技术 |

持续关注点：（质量、效率、成本）变更

## IEEE Standard 610.12-1990

## Software Engineering

![](img/fcdc64f47992afbcce2e20fafbbb0375_16_0.png)

SE工具：（半）自动化支持（CASE）

SE方法：如何做；基本原则

SE基础：过程

SE根基：质量关注点

软件工程基础是过程(process)！！！

## 二、软件全生命周期质量保障问题

## （1）何谓全生命周期软件质量保障？

•If we rely on testing alone, defects created first are detected last

![](img/fcdc64f47992afbcce2e20fafbbb0375_18_0.png)

这是软件生命周期后期阶段的质量保障！

## W - Whole Life Cycle

![](img/fcdc64f47992afbcce2e20fafbbb0375_19_0.png)

单个生命周期中每个阶段的质量保障！【传统线性开发】

![](img/fcdc64f47992afbcce2e20fafbbb0375_20_0.png)

多生命周期中每个生命周期的每个阶段的质量保障！（非线性开发，敏捷开发的基础理念）

## （2）全生命周期软件质量如何保证？

## Two Legs

## Software development

## Software defect / Fault detection
- Formal Specification
- SPI
- Architecture
- CMM
- UML
- ……

- Software analysis
- Software testing
- Software measure
- Formal verification
- Dynamic monitoring
- ……

## （3）软件质量与软件缺陷的关系-root cause analysis
- analysis
- testing
- measurement
- verification
- simulation
- prediction

## 内部质量

## 外部质量

Readability, understandability

Reliability, Testability…

Find Bugs

Code/Document /Model/Data quality

Software/system quality

maintainability, controllability, dead-free, error-prone, liveness… …

Safety, security, …

run-time monitoring

## 三、关注点牵引的科研选题

## （1）关注点牵引的科学研究选题

## 领域空间

## 质量问题空间

## 方法空间

对象计算

代码

文档

数据

服务计算

云计算

产品

代码质量

数据质量

设计质量

文档质量

需求质量

模型质量

分析方法

测试方法

验证方法

恢复方法

仿真方法

监控方法

- 确定选题的一般步骤：
- 1）找到您最熟悉也是最感兴趣的领域
- 2）分析最需要、也是您最有可能解决的问题
- 3）寻找您最有把握的问题解决方法
- 4）确定最终选题

问题：1）有价值；2）未（完全）解决
问题求解：1）老方法解决老问题；2）新方法解决老问题；3）老方法解决新问题；4）新方法解决新问题

## 代码质量问题的细化——举例

| 代码质量问题 | 问题发现方法举例 | 问题解决方法 |
|---|---|---|
| 复杂性问题 | 圈复杂度、Halstead复杂度 | Modification<br>Modularize<br>Refactor<br>Re-structure<br>Re-architecture<br>Re-configuration<br>Re-compile<br>Reverse Engineering<br>Re-engineering<br>Usage of patterns<br>…… |
| 一致性问题 | Conformance testing,<br>consistency checking |  |
| 兼容性问题 | 数据一致性、接口一致性检查 |  |
| 可维护性问题 | 可修改性分析、修改影响分析 |  |
| 可理解性问题 | 编码规范性检查 |  |
| 可扩展性问题 | 接口测试、内聚性度量 |  |
| 可集成性问题 | 接口测试、兼容性测试 |  |
| 信息流安全问题 | 信息流安全测试 |  |
| 可测试性问题 |  |  |
| …… |  |  |

|  |  |
|---|---|
| Understanding the API usage in Java | IST |
| A new method to encode calling contexts with recursions | SCIENCE CHINA |
| Efficient online cycle detection technique combining with Steensgaard points-to information | SPE |
| Incremental verification of evolving BPEL-based Web composite service | CJE |
| Regression Testing of Web Service: A Systematic Mapping Study | ACM Computing Surveys |
| Profiling Selected Paths with Loops | SCIENCE CHINA |
| PHAT: A Preference and Honesty Aware Trust Model for Web Services Trust Model for Web Services | IEEE TNSM |
| Verifying the Concurrent Properties in BPEL Based Web Service Composition Process | IEEE TNSM |
| FCA-CIA: An Approach of Using FCA to Support Cross-level Change Impact Analysis for Object Oriented Java Programs | IST |
| A Survey of Code-based Change Impact Analysis Techniques | STVR |
| Using Water Wave Propagation Phenomenon to Study Software Change Impact Analysis | ADES |
| Combining Concept Lattice with Call Graph for Impact Analysis | ADES |
| Profiling All Paths: A New Profiling Technique for Both Cyclic and Acyclic Paths | JSS |
| Automatic Test Case Selection for Regression Testing of Composite Service Based on Extensible BPEL Flow Graph | JSS |
| Combining Control Structure and Composition Condition for Web Services Reliability Prediction | CJE |
| HSM-based Change Impact Analysis of Object-Oriented Java Programs | CJE |
| Generating Test Case of Composite Services Based on OWL-S and EH-CPN | IISEKE |
| A Classification and Comparison of Model Checking Software Architecture Techniques | JSS |
| Timed Property Sequence Chart | JSS |
| Static change impact analysis techniques: A comparative study | JSS |
| MSR4SM: Using topic models to effectively mining software repositories for software maintenance tasks | IST |
| SE-FCA: A Model of Software Evolution with Formal Concept Analysis | CJE |
| Analyzing Impact Rules of Different Change Types to Support Change Impact Analysis | IISEKE |
| Change impact analysis and changeability assessment for a change proposal: An empirical study | JSS |
| Model and Verification of WS-CDL Based on UML Diagrams | IISEKE |
