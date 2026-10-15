
## 主要测试度量指标（续）

- 缺陷密度 = 缺陷数/软件规模
- 覆盖率
  - 测试需求覆盖率
  - 测试执行覆盖率
  - 用例通过覆盖率
  - 代码覆盖率
  - 功能覆盖率
- 缺陷分布
  - 按测试时间（趋势）
  - 按测试一定周期
  - 按软件开发组
  - 按缺陷严重性
  - 按缺陷状态

## 测试的文档

- 测试计划 —— 在测试计划阶段
- 测试用例文档 —— 在测试设计阶段
- 缺陷报告、测试记录 —— 在测试执行阶段
- 测试报告 —— 在测试完成后

## 测试的数据流

![](img/bd1e40ee9d51e0bf88db831d8e65a09d_339_0.png)

## 本节内容

- 测试概述
- 测试技术
- 测试策略
- 测试过程
- 自动化测试

## 自动化测试

- 工具类型
  - 单元测试工具，即白盒测试工具
  - 性能测试工具
  - 功能测试工具，即回归测试工具
  - 故障跟踪工具
  - 测试数据生成工具
  - 测试管理工具
  - 等
- 工具产品
  - HP Mercury：WinRunner，LoadRunner …
  - IBM Rational
  - Computer：QA Run，QA Load，QA Director …
  - Freeware：JUnit，selenium，Jmeter，Bugzilla …
  - ……

## 什么情况下适合用自动测试？

- 产品型项目
- 增量式开发、持续集成项目
- 能够自动编译、自动发布的系统
- 回归测试
- 多次重复的机械性动作，如性能测试
- 需要频繁运行的测试
- 将预项的任务转化为自动化测试

## 什么情况下不适合用自动测试

- 定制型项目（一次性的）
- 项目周期很短的项目
- 业务规则复杂的对象
- 美观、声学、易用性测试
- 测试很少运行
- 软件不稳定
- 涉及物理交互

## 自动化测试的误区

- 希望自动化测试能取代手工测试
  不能期望自动化测试来取代手工测试，测试主要是还要靠人做的。
- 预期自动测试发现大量新的缺陷
  事实证明新缺陷越多，自动化测试失败的几率就越大，发现更多的缺陷应该是手工测试的主要目的。测试专家James Bach 估计有 85%的缺陷靠手工发现，而自动化测试只能发现15%的缺陷。自动化测试能较好的发现老缺陷。

## 自动化测试的误区（续）

- 工具本身不具有想象力
- 工具毕竟是工具，出现一些需要思考、体验、界面美观方面的测试，自动化测试工具无能为力
- 技术问题、组织问题、脚本维护
  自动化测试的建立，有很多问题，比如组织是否重视，是否成立专门的测试团队，是否有这样的技术水平，对于测试脚本的维护工作量也很大的，是否值得维护等等问题都必须考虑。

## Software Engineering

## Lehman的8条软件演化法则

- （1974）持续变更法则。软件必须持续改进，否则就会变得越来越不令人满意。
- （1974）愈来愈快法则。软件的复杂性随着演化不断增加，除非采取措施使系统保持或降低复杂性。
- （1974）自调节法则。软件的演化过程可以由自动调节产品分布和过程熵，以接近正常状态。
- （1978）组织稳定法则。在软件的生命周期中，组织平均开发效率是稳定的。

## 软件演化和维护

- （1978）透明性法则。随著软件的庞大，所有相关人员（如开发人员、销售人员和用户）都必须始终掌握软件的内容和运行方式，以便达到满意的演化效果。软件的迅速增长会削弱对其内容和行为的透明度，因此软件保持动态增长的比率相对较低。
- （1991）功能持续增加法则。在软件的生命周期中，软件功能必须持续增加，否则用户满意度会降低。
- （1996）质量衰减法则。如果软件质量和适应性调整速度之迟缓超过运行环境的改变，软件的适应性和质量会降低。
- （1996）反饥饿法则。软件维护是长期、复杂、多主体和主体间系统相关，且要想在任何综合的系统基础上对有意义的改进就必须这样处理。

## 软件演化和维护

- 软件演化
- 软件维护

## 软件维护“冰山”

- 有关调查结果表明，软件维护是软件工程中最耗费资源的活动，很多软件公司中软件维护的成本已经达到了整个软件生命周期预算的40%到70%，甚至达到了90%。
- 软件系统趋于大型化和复杂化，大多数软件在设计时没有考虑到将来的修改问题，常常见到开发人员变更需求、文档不吻合、维护周期过长等问题，这些问题导致维护活动的时间与花费不断增加。

## 维护类型

|        | 种类 | 例子 |
|--------|------|------|
| 和维护相关的 | 纠错性维护 | 定位错误并修复 |
| 和演化相关的 | 完善性维护 | 适应性维护 |

- 纠错性维护（Corrective maintenance）
  - 由软件中缺陷引起的修复
- 完善性维护（Perfective maintenance）
  - 根据用户在使用过程中提出的一些建设性意见而进行的维护活动
- 适应性维护（Adaptive maintenance）
  - 为适应环境的变化而修改软件的活动
- 预防性维护（Preventive maintenance）
  - 为了进一步提高软件系统的可维护性和可靠性，并为以后的改进奠定基础

## 维护的技术问题

- 有限理解（Limited understanding）。对他人开发软件进行维护时，如何快速理解程序并找到需要修改或纠错的地方？
- 在软件维护过程中需要大量的回溯测试，耗时耗力。当软件非常关键以致不能停止时，如何进行在线维护而不影响软件的运行？
- 影响分析，如何对现有软件的变更所进行的全面分析？
- 如何在开发中促进和遵循软件的可维护性？
- 包括可分析性（Analyzability）、易改变性（Changeability）、稳定性（Stability）和易测试性（Testability）

## Software Engineering

## Appendix1 UML C++ Map

## 软件工程
Appendix: UML to C++ Mapping

## Mapping Representation: Notes

Course
// Notes will be used in the rest of the presentation;
// to contain C++ code for the attached UML elements
class Course {
public:
Course();
~Course();
};

## Visibility for Attributes and Operations

Student
- name : char*
+ addSchedule (thisSchedule: Schedule, thisSemester: Semester)
# hasPrerequisite (thisCourseOffering: CourseOffering): int
# exists (thisCourseOffering: CourseOffering): int
class Student {
public:
void addSchedule (thisSchedule: Schedule, thisSemester: Semester);
int hasPrerequisite (thisCourseOffering: CourseOffering): CourseOffering;
protected:
int exists (thisCourseOffering: CourseOffering);
private:
char* name;

## Class Scope Attributes and Operations

Student
- nextAvailID : int = 1
+ getNextAvailID() : int
class Student {
public:
static int getNextAvailID();
private:
static int nextAvailID = 1;
};

## Utility Class

- A grouping of "free" attributes and operations

<<utility>>
MathPack
- randomSeed : long = 0
- pi : double = 3.14159265358979
+ sin (angle : double) : double
+ cos (angle : double) : double
class MathPack {
public:
static double sin(double angle);
static double cos(double angle);
static double random();
private:
static long randomSeed = 0;
static double pi = 3.14159265358979;
};
void main(void)
{...}
myCos = MathPack::cos(90.0);

## Nested Class

- Hide a class that is relevant only for implementation

Outer
Outer::Inner
class Outer {
public:
class Inner {
public:
Inner();
~Inner();
};
Outer();
~Outer();
};

A1 - 1
