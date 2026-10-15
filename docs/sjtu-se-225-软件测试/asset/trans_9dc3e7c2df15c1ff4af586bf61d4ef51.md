

评审流程包含五个正式步骤：

- 在 **overview** 步骤中，模块的作者向团队进行演示。
- 在 **preparation** 步骤中，参与者尝试详细理解代码并编制按严重性(严重性)排序的问题清单。在此过程中，他们会得到一份潜在缺陷检查清单的帮助，以便留意这些缺陷。
- 在 **inspection** 步骤中，对代码进行彻底的逐行审查，旨在通过完整覆盖代码来发现缺陷。在检查后的一天内，主持人会制作一份细致（小心翼翼）的书面报告。
- 在 **rework** 步骤中，负责代码的个人解决书面报告中记录的所有缺陷和问题。（Individual Reviewer Issues Spreadsheet）
- 在 **follow-up** 步骤中，主持人必须确保每个问题都已通过修复代码或澄清令人困惑的点来解决。（Review Report Spreadsheet）

## Individual Reviewer Issues Spreadsheet

| <Work product information> |  |  |  |  |
| <Reviewer Name> |  |  |  |  |
| <Preparation Date> |  |  |  |  |
| <Reviewer Preparation Time> |  |  |  |  |
|  | Location | Checklist |  |  |
| Issue # | Page | Line | Item | Severity | Description |
| 1 | 1 | 18 | Typo | 1 | Change "accound" to "account" |

## Review Report Spreadsheet

| Review Team Members | Preparation Time | |
|---|---|---|
| Leader | | |
| Recorder | | |
| Reviewer | | |
| Reviewer | | |
| Reviewer | | |
| Reviewer | | |
|  | Total prep time | |
| Meeting date | | |

<Review Recommendation>

| Issue # | Reviewer | Location |  | Checklist |  | Description |
|---|---|---|---|---|---|---|
|  |  | Page | Line | Item | Severity |  |
| 1 |  | 1 | 18 | Typo | 1 | Change “accord” to “account” |

- 检查的一个重要成果是按严重程度评定的发现的缺陷数量和种类。([Here is a sample outline of a review report](#))
- 如果一个模块在检查中表现出比系统中其他模块显著更多的缺陷，它就是重写的良好候选者。
- 如果对两个或三个模块的检查显示出大量特定类型的错误，这可能需要（重新）检查其他模块是否存在类似错误。
- 如果超过 5% 的检查材料必须返工，团队必须重新召集进行全面复检。

## 3.2 Execution-based Verification

使用测试用例执行程序，获取执行的所有结果。

有两种基本的方法来测试模块，每种方法都有其自身的弱点。

- Testing to Specifications，也称为黑盒测试。
- Testing to Code，也称为玻璃盒、白盒测试。

### 3.2.1 Black-box test

![](img/8454895dcf92bedbe5b40d0487077d64_116_0.png)

- 寻求验证模块是否符合指定的输入和输出，同时忽略实际代码
- 很少可能对所有模块的所有可能的输入情况进行测试，这可能是一个巨大的模块数量

- 等价类测试是一种基于输入规范给出软件产品应以相同方式工作的值范围的想法而建立的技术。
- 边界值分析寻求使用位于等价类边界上以及边界两侧的输入值来测试产品。

例如输入是 (a,b)，至少有 5 个等价类：

![](img/8454895dcf92bedbe5b40d0487077d64_118_0.png)

**functional testing**，测试人员识别模块中实现的每个功能项或每个函数，并使用数据测试每个函数。

### 3.2.2 White-box test

![](img/8454895dcf92bedbe5b40d0487077d64_119_0.png)

- 也称为逻辑驱动或路径导向测试。
- 即使对于简单的流程图，测试代码中的每条路径通常也是不可行的。
- 此外，即使测试了每条路径也可能找不到现有缺陷，因为例如，缺陷在于选择路径之间的决策标准。

