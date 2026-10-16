
## 3c. Elaborate Attributes

- Analysis classes will typically only list names of general attributes (ex. paperType).
- List all attributes during component design.
- UML syntax:
    - `name : type-expression = initial-value { property string }`
- For example, paperType can be broken into weight, size, and color. The weight attribute would be:
    - `paperType-weight: string = "A" { contains 1 of 4 values – A, B, C, or D }`

## 3d. Describe Processing Flow

- Activity diagram for computePaperCost()

![](img/fcdc64f47992afbcce2e20fafbbb0375_298_0.png)

## Step 5 – Elaborate Behavior

- It is sometimes necessary to model the behavior of a design class.
- Transitions from state to state have the form:
    - Event-name (parameter-list) [guard-condition] / action expression

![](img/fcdc64f47992afbcce2e20fafbbb0375_300_0.png)

## Step 6 — Elab. Deployment

- Deployment diagrams are elaborated to represent the location of key packages or components.

![](img/fcdc64f47992afbcce2e20fafbbb0375_301_0.png)

## Step 7 — Redesign/Reconsider

- The first component-level model you create will not be as complete, consistent, or accurate as the nᵗʰ iteration you apply to the model.
- The best designers will consider many alternative design solutions before settling on the final design model.

## Chapter 15

Product Metrics for Software

Software Engineering: A Practitioner's Approach, 6th edition
by Roger S. Pressman

### 本章要点

- 软件质量
- 产品度量
    - 分析度量
    - 设计度量
    - 代码度量
    - 测试度量

### 概述

- 产品度量有助于软件工程师对其设计和构造的软件获得深层次的了解。
- 产品度量为分析、设计、编码和测试能更客观地执行和更定量的评估提供基础。
- 与项目度量和过程度量不同【第22章】。

### 15.1 软件质量

- 一般来讲，软件质量是对明确陈述的功能和性能需求、明确记录的开发标准以及对所有专业化软件开发应具备的隐含特征的符合度。
    - 软件需求是质量测量的基础，不符合需求就是没有质量。
    - 若未能遵守开发准则，则肯定质量有问题。
    - 若软件符合显式需求，但未能满足其隐式需求，则软件质量仍然值得怀疑。

#### McCall’s Triangle of Quality

Maintainability[可维护性]
Flexibility[灵活性]
Testability[可测试性]

Portability[可移植性]
Reusability[可复用性]
Interoperability[互操作性]

PRODUCT REVISION

PRODUCT TRANSITION

PRODUCT OPERATION

Correctness  Usability  Efficiency
Reliability  Integrity

![](img/fcdc64f47992afbcce2e20fafbbb0375_307_0.png)

#### A Comment

McCall’s quality factors were proposed in the early 1970s. They are as valid today as they were in that time. It’s likely that software built to conform to these factors will exhibit high quality well into the 21st century, even if there are dramatic changes in technology.

### ISO 9126质量因素

- 功能性: Functionality
- 可靠性: Reliability
- 易用性: Usability
- 效率: Efficiency
- 可维护性: Maintainability
- 可移植性: Portability

### 度量原则

- **设定度量目标**: The objectives of measurement should be established before data collection begins;
- **定义要明确**: Each technical metric should be defined in an unambiguous manner;
- **有效理论支持**: Metrics should be derived based on a theory that is valid for the domain of application (e.g., metrics for design should draw upon [利用] basic design concepts and principles and attempt to provide an indication of the presence of an attribute that is deemed desirable);
- **度量指标的选择要是最合适的**: Metrics should be tailored to best accommodate specific products and processes.

### 典型度量过程

- **Formulation【公式化】**. The derivation of software measures and metrics appropriate for the representation of the software that is being considered.
- **Collection【收集数据】**. The mechanism used to accumulate data required to derive the formulated metrics.
- **Analysis【分析结果】**. The computation of metrics and the application of mathematical tools.
- **Interpretation【解释评估】**. The evaluation of metrics results in an effort to gain insight into the quality of the representation.
- **Feedback【反馈】** Recommendations derived from the interpretation of product metrics transmitted to the software team.
