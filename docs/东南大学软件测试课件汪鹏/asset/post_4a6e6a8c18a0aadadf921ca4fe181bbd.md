
## 非功能系统测试

## 可使用性和易获得性测试

易获得性：
检查产品对于行动不便的用户也可使用的测试

基本以获得性：
粘贴键、声响键、多种模拟鼠标功能、朗读器、触摸...

## 非功能系统测试

## 国际化测试

目的：
确保软件支持不同国家语言的测试手段

国际化问题：
语言的消息显示
语言和习俗的消息处理
日期格式、货币格式
对话框等文本显示区域至少0.5被宽度的扩展空间
......

## 国际化生活的体验

- 去美国旅行，最感不适应会有什么？
- 2/3/2009 代表哪一天，2月3日或3月2日？
- 乔治·布什（George Bush）属什么生肖？

![](img/88f667f5480db09ef600e4e177b09268_478_0.png)

## 具体例子

【中文简体，北京】
开始日期：2008年12月1日
开始时间：8:00，中国标准时间（GMT +08:00）

【英文、纽约】
Starting date: Sunday, November 30, 2008
Starting time: 7:00 pm, Eastern Standard Time (GMT -05:00)

![](img/88f667f5480db09ef600e4e177b09268_478_1.png)

## 示例—阿拉伯语

![](img/88f667f5480db09ef600e4e177b09268_478_2.png)

## 二 确认测试/验收测试

## 1. 确认测试概念

![](img/88f667f5480db09ef600e4e177b09268_479_0.png)

## 确认测试

## 概念

**定义：** 检查产品是否满足在项目的需求阶段定义的**确认准则**，或者说是否具备在真实环境中使用的条件

**实施者：** 客户或客户代表

**引入时机：** 系统测试之后

![](img/88f667f5480db09ef600e4e177b09268_480_0.png)

## 确认测试

## 确认准则

产品确认：
对现有测试用例进行分类形成确认准则

规程确认：
文档、发布介质、使用培训

服务等级约定：
例如：前三个月内发现的重要缺陷应免费修改

## 确认测试

## 选择确认准则的测试用例

**建议：**

- 端到端的功能验证：所有事务测试都在客户端进行
- 领域测试用例：反映业务领域知识
- 用户场景测试用例：反映真实用户场景
- 完善性测试用例：全面包含各项功能

## 确认测试

## 选择确认准则的测试用例

建议：

- 新功能：检验新功能
- 少量非功能测试用例：再次验证非功能特性
- 符合法规义务和服务约定的测试用例
- 确认测试数据：选择客户真实数据

## 确认测试

## 执行确认测试

开发组织：
辅助客户完成确认测试

确认测试团队：
产品管理层+支持团队+咨询团队
90%成员：具有产品业务过程知识
10%成员：技术测试团队

开发组织的测试团队：
与确认测试团队不断沟通，提供采集测试数据和分析测试结果的帮助

## 三 回归测试

- 1. 回归测试概念
- 2. 波及效应

![](img/88f667f5480db09ef600e4e177b09268_485_0.png)

## 开发人员的一天

Rainbow Build: 2261 has been build SUCCESSFULLY and PASSED BVT tests - Message (Rich Text)

From: Rainbow Build Automation
To: Rainbow Project Team All Members
Cc:
Subject: Rainbow Build: 2261 has been build SUCCESSFULLY and PASSED BVT tests

Rainbow Build 2261 has been build SUCCESSFULLY and PASSED the BVT tests.

Build Information
Build No. 2261
Build Started 06/29/2004 04:00 AM
Build Finished 06/29/2004 04:20 AM
Build Result Passed
Location \\rainbow02\build\drops\2261
MSI Tested \\rainbow02\build\drops\2261\distrib\retail\RainbowInstaller.msi
Other Comments

Summary of BVT Tests
No. of Test Cases Executed 4
No. of Test Cases Passed 4
No. of Test Cases Failed 0

For Detailed Results, visit:
http://rainbowteam/build/BVT/Default.aspx

Thank you,
Rainbow Test Team

This is an automated Daily Build message generated from an unmonitored alias.
DO NOT REPLY to this alias.
For Further information on results, please contact Rainbow Test Team.
For Build Information, please contact Rainbow Build Distribution.

Build Quick Status

Drop Location

Summary Results

Detailed Results URL

## 接下来，开发人员会...

- 从源代码管理工具中Check out代码
- 修改代码（解决Bug或实现新功能）
- 取得源代码管理工具中最新变化，在本机Build和单元测试
- 请开发组同事作Code Review
- Check in代码
- 在Bug管理工具中修改Bug的状态
- 开发人员以一封Daily Report结束一天的工作

## 启示：软件每天都在成长变化

问题1：软件修改会对周围/之前的模块有何影响？

问题2：用什么测试手段保证软件在不断修改过程中的功能完整性和正确性？

## 回归测试基础

## 回归测试背景

## 琢磨不定的软件

- 1. 它总是在变化：**软件不断演化**——开发、维护、升级
- 2. 对它的要求从未停止：软件**需求不断变更**
- 3. 它还要适应不断变化的环境：**技术更新和软/硬件升级**

**软件的每次改变都会引入潜在风险——缺陷**

## 回归测试基础

## 回归测试背景

## 对软件变化的要求

- 1. 修改后的功能是否达到预期？
- 2. 原有功能是否被损害？

解决方案：回归测试是一种验证已变更系统的完整性与正确性的测试技术

## 回归测试基础

## 回归测试概念

回归测试(Regression Testing)：

定义1：回归测试是对之前已测试过、经过修改的程序进行的重新测试，以保证该修改没有引入新的错误或者由于更改而发现之前未发现的错误。

定义2：回归测试要保证增强型或改正型修改使软件正常进行并且不影响已有的功能。

## 回归测试基础

## 回归测试概念

## 回归测试意义：

- 1. 保证软件维护时未更改的代码功能不会受到影响
- 2. 保证软件模块区域和持续维护过程与回归测试的协作关系，使回归测试成为一个每月/每周/每日的常规活动
- 3. 实现软件整个生命周期的测试

## 回归测试基础

## 回归测试概念

## 回归测试特点：

- 1. **测试计划**
  - 常规测试：已有的带有测试用例的测试计划
  - 回归测试：更改的规格说明书、修改过的程序和需要更新的旧测试计划

- 2. **测试范围**
  - 常规测试：整个程序
  - 回归测试：被修改部分正确性以及它与原有功能的整合

- 3. **时间分配**
  - 常规测试：测试时间实现有预算
  - 回归测试：测试时间不包含在进度表中

## 回归测试基础

## 回归测试概念

## 回归测试特点：

- 4. 开发信息
  常规测试：随时可获得开发信息
  回归测试：需要保留开发信息保证回归测试正确

- 5. 完成时间
  常规测试：所需时间长
  回归测试：只需测试软件的一部分，所需时间短

- 6. 执行频率
  常规测试：高频率的活动
  回归测试：由系统被修改而触发的周期性活动
