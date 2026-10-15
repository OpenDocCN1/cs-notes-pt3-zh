
## Software Engineering / 软件工程

## 软件过程

![](img/bd1e40ee9d51e0bf88db831d8e65a09d_21_0.png)

## 需求工程

Module: 需求工程

Shanghai Jiao Tong University  
上海交通大学软件工程中心

### 问题

- 用户说不清需求
- I'm not sure, but I'll know it when I see it
- 需求经常变化，项目没有时间
- 开发人员不断地大量超时工作，因为误解或二义性的需求直到开发后期才发现
- 系统测试白费了，因为测试者并未明白产品要做什么
- 功能都实现了，但由于产品的低性能、使用不方便或其它因素用户不满意
- 维护费用相当高，因为客户的许多增加要求未在需求获取阶段提出

### 需求工程

- 软件需求概念
- 需求获取
- 需求分析和建模
- 需求定义和验证
- 需求管理

@第5章 教材

### 什么是软件需求？

![](img/bd1e40ee9d51e0bf88db831d8e65a09d_22_0.png)

### 定义

- 需求
  - 系统必须符合的条件或能力
- 软件需求
  - 用户对目标软件系统在功能、行为、性能、设计约束等方面的期望。
- 内容包括：FURPS+

关注 What!

### FURPS

|  |  |  | 功能需求 |
|---|---|---|---|
| Functionality | Feature Set Capabilities | Generality |  |
|  | Security | Security |  |
| Usability | Human Factors | Consistency |  |
|  | Aesthetics | Documentation |  |
| Reliability | Frequency/Severity of Failure | Predictability | 非功能需求 |
|  | Recoverability | Accuracy |  |
|  | MTBF |  |  |
| Performance | Speed | Throughput |  |
|  | Efficiency | Response Time |  |
|  | Resource Usage |  |  |
| Supportability | Testability | Configurability |  |
|  | Extensibility | Serviceability |  |
|  | Adaptability | Installability |  |
|  | Maintainability | Localizability |  |
|  | Compatibility | Robustness |  |

### 定义 Functionality 需求

概要功能需求

Feat 63 - the defect tracking system will provide trending information to help the project manager assess project status

详细功能需求

Trending information will be charted with a line graph showing time on the x axis, and number of defects found on the y axis.

### 定义 Reliability 需求

- “reliability”可靠性
  - The ability for the software to behave consistently in a user-acceptable manner
- 可靠性需求
  - Availability (xx.xx%)
  - Accuracy
  - Mean time between failures (xx hrs)
  - Max. bugs per KLOC (0-x)
  - Bugs by class - critical, significant, minor

### 定义 Supportability 需求

- “supportability”支持性
  - The ability of the software to be easily modified to accommodate enhancements and repairs
- 支持性需求
  - Languages, DBMSs, tools, etc.
  - Programming standards
  - Error handling and reporting standards
- 常常难以定义
  - If it is not measurable or observable, it is not a requirement
  - Is it a design constraint?
  - Is it an intent or goal?

### 定义 Performance 需求

- “performance”性能
  - A measure of speed or efficiency of the running system
- 性能需求
  - Capacity
  - Throughput
  - Response time
  - Memory
  - Degradation modes
  - Efficient use of scarce resources
    - Processor, memory, disk, network bandwidth

### 定义 Usability 需求

- “usability”可用性
  - The ease with which software can be learned and operated by the intended users
- 可用性需求
  - Training time requirements, measurable task times
  - User abilities (beginner/advanced)
  - Comparison to other systems that users know and like
  - Online help systems, tool tips, documentation needs
  - Conformity with standards
    - Examples: Windows, style guides, GUI Standards

### FURPS +

- 设计约束（design constraints）：规定或约束了系统设计的需要
- 实现需求（implementation requirements）：规定或要求了系统的编码或构造，如所需的标准、编程语言、数据库完整性策略、容错限制和操作环境。
- 接口需求（interface requirements）：规定了系统必须与之交互的外围软硬件，以及对这种交互作用所使用的格式、时间或其他因素的约束。
- 物理需求（physical requirements）：规定了系统必须具备的物理特征，可用来代表硬件要求，如物理网络配置需求。

### 二义性练习

我没说她偷了我的钱

Mary had a little lamb

如何减少需求的二义性？

### 需求工程

### 二义性与可理解性的关系

![](img/bd1e40ee9d51e0bf88db831d8e65a09d_25_0.png)

### 可验证性

- 需求是可验证的，如果可以用人工或机器方法检查产品是否满足需求
- The system supports up to 1,000 simultaneous users
- The system shall respond to an arbitrary query in 500 msec.
- The color shall be a pleasing shade of green
- The system shall be available 24 x 7
- The system shall export view data in comma-separated format

这些需求可验证吗？如果不，如何更好地表述？

### 需求出错的高成本

The 1-10-100 Rule

![](img/bd1e40ee9d51e0bf88db831d8e65a09d_25_1.png)

> "All together, the results show as much as a 200:1 cost ratio between finding errors in the requirements and maintenance stages of the software lifecycle."

### 需求工程

![](img/bd1e40ee9d51e0bf88db831d8e65a09d_25_2.png)

发现、获取、组织、分析、编写和维护需求的方法论，让客户和项目之间沟通共享

### 需求工程

- 软件需求概念
- 需求获取
- 需求分析和建模
- 需求定义和验证
- 需求管理
