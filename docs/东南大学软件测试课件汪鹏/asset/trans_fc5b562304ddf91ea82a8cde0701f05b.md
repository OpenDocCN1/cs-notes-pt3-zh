

## 1988–Now – 面向预防的时代
面向预防

- 测试理论和技术进一步完善
- 测试工具发展迅速，大大提高测试的自动化程度
- 商业化软件测试工具和开源软件测试工具。
- Web测试，面向对象测试,测试脚本开发......

## Software Testing Timeline
软件测试时间线

http://www.testingreferences.com/testingtimeline/testingtimeline.jpg

![](img/88f667f5480db09ef600e4e177b09268_66_0.png)

### Legend
图例

- Companies and organisations
公司和组织
- Conferences
会议
- Education and certification
教育和认证
- Literature
文献
- Models and standards
模型和标准
- Publications and ideas
出版物和思想
- Tools and applications
工具和应用

## 软件测试背景

## 软件测试的意义  软件缺陷难以避免！

## ② 火星登陆事故(Mars Polar Lander)

![](img/88f667f5480db09ef600e4e177b09268_67_0.png)

> Nancy G. Leveson, *The Role of Software in Spacecraft Accidents*
> Nancy G. Leveson, *《航天器事故中的软件作用》*

## 启发：集成测试的必要性

## 软件测试背景

## ■ 软件测试的意义　**软件缺陷难以避免！**

## ③ 千年虫问题(Y2K)

![](img/88f667f5480db09ef600e4e177b09268_68_0.png)

今天的编程课讲到rand()时，讲到可以用Unix Timestamp来做随机数发生器的种子，讲而讲到因为Unix Timestamp用32位int表示造成的「2038年」问题。所有基于Unix Timestamp的计算机程序，大到云数据库小到智能温度计，都会在2038年1月19日凌晨3点14分07秒回到1901年。也许这是计算机设计史上最大的失误。

## 软件测试背景

## 软件测试的意义  软件缺陷难以避免！

## 爱国者导弹防御系统

启发：缺陷难以发现(可靠性测试)

![](img/88f667f5480db09ef600e4e177b09268_69_0.png)

## 软件测试背景

## 软件测试的意义　软件缺陷难以避免！

## 5　Intel奔腾处理芯片缺陷(Pentium FDIV bug)

![](img/88f667f5480db09ef600e4e177b09268_70_0.png)

Thomas Nicely

![](img/88f667f5480db09ef600e4e177b09268_70_1.png)

(4195835/3145727) *3145727-4195835

4195835.0/3145727.0 = 1.333 820 449 136 241 002 (Correct value)
4195835.0/3145727.0 = 1.333 739 068 902 037 589 (Returned by flawed Pentium)
4195835*3145727/3145727 = 4195835 (Correct value)
4195835*3145727/3145727 = 4195579 (The flawed Pentium)

http://en.wikipedia.org/wiki/Pentium_FDIV_bug

芯片界那点破事 http://weibo.com/tarticle/p/show?id=230940399088803651075#_0

## 软件测试背景

## ■ 软件测试的意义　**软件缺陷难以避免！**

## ⑥ 北京奥运订票网站瘫痪

**事故过程：**订票系统半小时即瘫痪

![](img/88f667f5480db09ef600e4e177b09268_71_0.png)

## 软件测试背景

## 软件测试的意义  软件缺陷难以避免！

Michael Jackson逝世消息
事故过程：百万网友同时在线疯狂查询修改美国流行天王迈克尔杰克逊逝的信息……

启发：性能测试在互联网应用中的重要性

![](img/88f667f5480db09ef600e4e177b09268_72_0.png)

## 软件测试背景

为什么会出现软件缺陷

- 一、 产品说明书(需求) (主要原因)
- 随意、易变、沟通不足
- 二、 设计 (次要原因)
- 随意、易变、沟通不足
- 三、 编码
- 软件复杂度，进度压力，低级错误
- 四、 其它
- 理解错误，测试错误

![](img/88f667f5480db09ef600e4e177b09268_73_0.png)

## 软件测试背景

## 软件测试的意义

软件测试是保证软件质量的重要手段。
软件测试深入软件开发过程的每个阶段，在有限的开发条件下，最大程度地保证最终软件产品符合用户需要。

## 二 软件测试基本概念

- 1. 软件测试是什么？
- 2. 软件测试活动需要遵循哪些原理？
- 3. 如何实施软件测试？
- 4. 软件测试如何分类？

## 软件测试基本概念

## ■ 软件测试的目的

**1.确保软件质量**

找出软件错误和缺陷，降低软件发布后潜在错误和缺陷造成的损失，验证软件是否能满足用户需求，树立对软件的信心。

**2.确保软件开发过程方向的正确性**

通过测试报告提供有用的数据帮助管理者做出正确判断，修正软件开发过程。

## 软件测试基本概念

理解Bug：Fault(失效) Error(错误) Failure(失败)

## Bug的定义：

- **Software Fault**: A static defect in the software (i.e., defect)
**软件缺陷**：软件中的静态缺陷（即缺陷）
- **Software Error**: An incorrect internal state that is the manifestation of some faults
**软件错误**：某些缺陷表现出来的不正确内部状态
- **Software Failure**: External, incorrect behavior with respect to the requirements or other description of the expected behavior
**软件失效**：相对于需求或其他预期行为描述的外部、不正确行为

## 软件测试基本概念

## 理解Bug：Fault(失效) Error(错误) Failure(失败)

Programmer makes a mistake.
程序员犯了错误。

Fault (defect, bug) appears in the program.
程序中出现了缺陷（缺陷、bug）。

Fault remains undetected during testing (running test inputs).
缺陷在测试期间未被检测到（运行测试输入）。

The program fails (based on test oracles) during execution i.e., it behaves unexpectedly.
程序在执行期间失效（基于测试 oracle），即行为异常。

Error: difference between computed, observed, or measured value or condition and true, specified, or theoretically correct value or condition
错误：计算、观察或测量的值或条件与真实、指定或理论上正确的值或条件之间的差异

## 软件测试基本概念

## 软件测试的原理/原则/准则

**原理1：用户需求至上**

所有测试都应追溯到用户需求。最严重的错误是导致软件无法满足需求的错误。

**原理2：测试是有计划的活动**

测试计划制定先于测试的执行；测试贯穿于全部软件生命周期。

## 软件测试基本概念

## 软件测试的原理/原则/准则

## 原理3：缺陷出现的集群性

软件缺陷会集中出现;80%的错误可能起源于20%的模块。

## 原理4：测试应从 “小规模” 走向 “大规模”

## 软件测试基本概念

## 软件测试的原理

**原理5：穷尽测试不可能**

可能对解二次方程穷尽测试吗？

```
class Roots {
    // Solve ax² + bx + c = 0
    public roots(double a, double b, double c)
    { ... }

    // Result: values for x
    double root_one, root_two;
}
```

**原理6：有效的测试应由第三方独立进行**

## 软件测试基本概念

## 软件测试的原理

原理7：测试无法揭示所有缺陷

测试只能说明缺陷存在，而不能说明软件没有缺陷。

原理8：测试的杀虫剂悖论

潜在缺陷对已进行的测试具有免疫力

