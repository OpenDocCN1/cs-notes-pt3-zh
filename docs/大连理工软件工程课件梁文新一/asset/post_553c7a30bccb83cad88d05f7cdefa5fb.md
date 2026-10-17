
## 1.4.6 Rational统一过程(RUP)

- Rational Unified Process (RUP)，Rational软件公司(2002年底被IBM收购)
  - 面向对象软件工程的通用业务流程
  - 为在开发组织中分配任务和职责提供了一种规范方法
  - 目标是确保在可预计的时间安排和预算内开发出满足最终用户需求的高品质的软件
  - 有一套过程框架(Process Framework)，各个组织可根据自身的实际情况和项目规模对RUP进行裁剪和修改，以制定出合乎需要的软件工程过程

### Best Practices

![](img/576b58d2c10334d3487443b8cc7c5551_59_0.png)

- Develop Iteratively
- Manage Requirements
- Use Component Architectures
- Model Visually (UML)
- Continuously Verify Quality
- Manage Change

## RUP建模元素

### 四种基本元素

- 角色（Workers）：Who
  - 完成工作的角色，定义他们应履行的行为和职责
- 活动（Activities）：How
  - 定义了工作人员如何执行工作
- 制品（Artifacts）：What
  - 由活动所产生、修改或使用的一种信息（管理集、需求集、设计集、实现集和实施集）
- 工作流（Workflows）：When
  - 描述生成制品的活动序列，用以描述工作人员之间的交互
  - 6个核心过程工作流和3个核心支持工作流

## 核心工作流 (Core Workflows)

### 核心过程工作流

1. 业务建模 (Business Modeling): 了解使用目标系统的机构及其商业运作，评估目标系统对该机构的影响
2. 需求 (Requirements): 捕获用户需求，定义系统构想，使用用例模型和补充规格说明定义系统软件需求，管理系统范围和需求变更
3. 分析和设计 (Analysis & Design): 研究实现环境和系统构件的效用，定义软件的组织结构，把需求获取结果转化为分析模型和设计模型
4. 实现 (Implementation): 建立代码的分层结构，用构件实现类和对象，把设计模型转化为实现结果，进行单元测试和系统集成
5. 测试 (Test): 根据事先定义的度量和准则检查各个子系统的交互与集成，验证所有需求是否正确实现，确认系统缺陷并确保在软件部署之前消除缺陷
6. 部署 (Deployment): 在实际使用环境中测试软件、包装要交付的软件、发布软件产品、培训最终用户及销售人员

### 核心支持工作流

7. 配置和变更管理 (Configuration & Change Management): 跟踪并维护在软件开发过程中产生的所有制品的完整性和一致性
8. 项目管理 (Project Management): 提供项目管理框架，为软件开发项目制定计划、人员配备、执行和监控准则，并为风险分析提供框架
9. 环境 (Environment): 向软件开发机构提供软件开发环境，包括过程管理和工具支持

## RUP开发过程阶段

- RUP把软件生命周期划分为四个连续的阶段
  - 初始阶段 (Inception Phase)
  - 精化阶段 (Elaboration Phase)
  - 构建阶段 (Construction Phase)
  - 移交阶段 (Transition Phase)

## 初始阶段 (Inception Phase)

### 主要目标

- 建立项目的软件规模和边界条件，包括运作前景、验收标准以及希望产品中包括和不包括的内容
- 识别系统的关键用例
- 对比一些主要场景，展示至少一个备选构架
- 评估整个项目的总体成本和进度
- 评估潜在的风险（源于各种不可预测因素）
- 准备项目的支持环境

### 主要成果

- 产品蓝图文档，即关于项目的核心需求、关键特性、主约束的总体蓝图
- 初始的用例模型（约占总体的10%~20%）
- 初始的项目术语表
- 初始的商业案例，包括商业环境、验收标准等
- 初始的风险评估
- 项目计划
- 一个或多个原型

## 精化阶段 (Elaboration Phase)

### 主要目标

- 确保构架、需求和计划足够稳定，充分减少风险，从而能够有预见性地确定完成开发所需的成本和进度
- 处理在构架方面具有重要意义的所有项目风险
- 建立一个已确定基线的构架
- 制作产品质量构件的演进式原型
- 证明已建立基线的构架将在适当时间、以合理的成本支持系统需求
- 建立支持环境（创建开发案例、创建模板和指南、安装工具）

### 主要成果

- 用例模型(至少完成80%)，所有的用例和参与者都已被识别出，并完成大部分的用例描述
- 补充非功能性要求以及与特定用例没有关联的需求
- 软件体系结构的描述
- 可执行的软件原型
- 修订过的风险清单和商业案例
- 整个项目的开发计划，该开发计划应体现迭代过程和每次迭代的评价标准
- 更新的开发案例
- 初步的用户手册

## 构建阶段 (Construction Phase)

### 主要目标

- 完成所有所需功能的分析、开发和测试
- 迭代式、递增式地开发，为部署应用程序作好准备

### 主要成果

- 开发出可以交付给最终用户的产品，它至少包括：
  - 集成于适当操作系统平台上的软件产品
  - 用户手册
  - 当前版本的描述

## 移交阶段 (Transition Phase)

### 主要目标和成果

- 确保最终用户可以使用软件
- 培训用户、维护人员和销售人员
- 根据产品的完整前景和验收标准进行评估

## RUP软件开发生命周期

| Phases | Inception | Elaboration | Construction | Transition |
|---|---|---|---|---|
| Workflows |  |  |  |  |
| Business Modeling |  |  |  |  |
| Requirements |  |  |  |  |
| Analysis & Design |  |  |  |  |
| Implementation |  |  |  |  |
| Test |  |  |  |  |
| Deployment |  |  |  |  |
| Configuration & Change Mgmt |  |  |  |  |
| Project Management |  |  |  |  |
| Environment |  |  |  |  |
| Iterations | Initial | Elab #1, Elab #2 | Const #1, Const #2, Const #N | Tran #1, Tran #2 |

## 敏捷软件开发

2001年2月11-13日，17位软件开发方法专家聚集在美国Utah州东北部Wasatch mountains里的一个叫Snowbird ski resort，一起交谈、讨论、寻找共同话题。通过交谈与会代表发现了他们所使用的方法确实存在着许多共同点，希望能将这些共同点记录下来，也希望记录下来的文档能拉响软件工业的战斗号角

虽然这些方法过去常被人称之为“轻载方法”（Lightweight Methods），但该名字并不足以代表这些方法的共性。会议的结果是将这些软件方法正式命名为敏捷开发方法（Agile Development Methodology），同时组建了敏捷联盟（Agile Alliance）
