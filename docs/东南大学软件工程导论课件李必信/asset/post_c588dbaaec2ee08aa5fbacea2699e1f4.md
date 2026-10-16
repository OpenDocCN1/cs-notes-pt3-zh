
## Typical Project Metrics

- **Effort/time** per software engineering task
- **Errors uncovered** per review hour
- Scheduled vs. actual **milestone dates**
- **Changes** (number) and **their characteristics**
- **Distribution of effort** on software engineering tasks

## Chapter 23

## Estimation for Software Projects

Software Engineering: A Practitioner’s Approach, 6th edition

by Roger S. Pressman

## 本章要点

- 项目估算

## 项目的哪些属性可以进行估算

软件项目的属性有很多，建议至少以下属性要在项目计划时对其进行估算：

- 1、项目规模
- 2、项目工作量
- 3、项目所需资源
- 4、项目各阶段工作量
- 5、项目成本

## Software Project Planning

The overall goal of project planning is to establish a **pragmatic strategy**[务实的策略] for controlling, tracking, and monitoring a complex technical project.

Why?

So the end result gets done on time, with quality!

## Project Planning Task Set-I

- Establish project scope
- Determine feasibility
- Analyze risks
- Define required resources
  - Determine require human resources
  - Define reusable software resources
  - Identify environmental resources

## Project Estimation Basis

![](img/fcdc64f47992afbcce2e20fafbbb0375_362_0.png)

- Project scope must be understood
- Elaboration (decomposition) is necessary
- Historical metrics are very helpful
- At least two different techniques should be used
- Uncertainty is inherent in the process

## Estimation Techniques

- **主观和客观方法**
- Past (similar) project experience
- Conventional estimation techniques
  - task breakdown and effort estimates
  - size (e.g., FP) estimates
- Empirical models
- Automated tools

![](img/fcdc64f47992afbcce2e20fafbbb0375_363_0.png)

![](img/fcdc64f47992afbcce2e20fafbbb0375_363_1.png)

## Empirical Estimation Models

General form:

```
effort = tuning coefficient * size^exponent
```

usually derived as person-months of effort required

either a constant or a number derived based on complexity of project

usually LOC but may also be function point

exponent
empirically derived

## COCOMO-II

COCOMO，英文全称为constructive cost model，中文为构造性成本模型。它是一种精确、易于使用的、基于模型的成本估算方法，最早由勃姆（Boehm）于1981年提出。从本质上说是一种参数化的项目估算方法，参数建模是把项目的某些特征作为参数，通过建立一个数字模型预测项目成本（类似于居住面积作为参数计算的整体的住房成本）。

![](img/fcdc64f47992afbcce2e20fafbbb0375_365_0.png)

![](img/fcdc64f47992afbcce2e20fafbbb0375_365_1.png)

## The Software Equation

A dynamic multivariable model

**E = [LOC × B^0.333/P]^3 × (1/t^4)**

where

- **E = effort in person-months or person-years**
- t = project duration in months or years
- B = “special skills factor”
- P = “productivity parameter”

## Estimation for OO Projects

- Develop estimates using effort decomposition, FP analysis, and any other method that is applicable for conventional applications.
- Using object-oriented analysis modeling (Chapter 8), develop use-cases and determine a count.
- From the analysis model, determine the number of key classes (called analysis classes in Chapter 8).
- Categorize the type of interface for the application and develop a multiplier for support classes:
  - Interface type
  - No GUI
  - Text-based user interface
  - GUI
  - Complex GUI

| Interface type | Multiplier |
|---|---|
| No GUI | 2.0 |
| Text-based user interface | 2.25 |
| GUI | 2.5 |
| Complex GUI | 3.0 |

## Estimation for Agile Projects

- Each user scenario (a mini-use-case) is considered separately for estimation purposes.
- The scenario is decomposed into the set of software engineering tasks that will be required to develop it.
- Each task is estimated separately. Note: estimation can be based on historical data, an empirical model, or “experience.”
  - Alternatively, the ‘volume’ of the scenario can be estimated in LOC, FP or some other volume-oriented measure (e.g., use-case count).
- Estimates for each task are summed to create an estimate for the scenario.
  - Alternatively, the volume estimate for the scenario is translated into effort using historical data.
- The effort estimates for all scenarios that are to be implemented for a given software increment are summed to develop the effort estimate for the increment.
