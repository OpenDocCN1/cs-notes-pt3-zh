

## 软件工程
## 示例：活动图
![](img/bd1e40ee9d51e0bf88db831d8e65a09d_54_0.png)

## 面向对象分析
## 分区
![](img/bd1e40ee9d51e0bf88db831d8e65a09d_54_1.png)

## 前置条件
- Use-case 启动的约束条件
- 不是触发 Use-case 的事件
- 可选的: 仅当需要时才用

示例:
必须满足下面的前置条件，ATM 系统才能出钞：
ATM 必须进入 ATM 网络。
ATM 必须与银行交易服务器的状态。
ATM 中必须有...现金可供出钞。
ATM 必须有足够的纸张打印至少一次交易的收据

## 后置条件
- 当用例 case 结束时，后置条件一定为真
- 用于降低用例事件流的复杂性并提高其可读性
- 还可用来描述在用例结束时系统执行的动作
- 可选的: 仅当需要时才用

示例:
在用例结束时如果显示 “欢迎使用” 消息，可将此消息记录在用例后置条件中。
与安全性：如果 ATM 在如现金短缺的情况下结束且总会禁止客户交易，则不管事件进程如何，将这种情况记录为用例后置条件。

## 其它 Use Case 属性
- 非功能需求
  - 有关本 use case 的 URPS+
- 业务规则
  - 在执行事件流时，使用到的重要业务规则或计算公式
- 扩展
  - use-case 可以通过另一 use-case 进行扩展
- 关联
  - 和 actors 及 use-case 的关联
- Use-case 图
  - 涉及本 use-case 的关系的可视化模型
- Other diagrams or enclosures
  - 交互、活动或其他图
  - 用户界面框图

## 面向对象分析的步骤
- 1. 用例建模
- 1.1 识别 actor 和 use case，画 Use-Case 图
- 1.2 编写 Use-Case Spec.
- 1.3 优化 Use-Case 图的结构
- 2. 建立概念模型
- 3. 用例分析

## Use Case 间的关系
- Include 包含
- Extend 扩展
- Generalization 泛化

## 什么是 Include 关系？
- 基本用例包含某个包含用例
- 包含用例定义的行为将显式插入基本用例

## Include 关系示例
Get Quote Use Case
1. Include "Identify Customer" to verify customer's identity
2. Display options. Customer selects "Get Quote"
3. ...

Identify Customer Use Case
1. Log on
2. Validate logon
3. Enter password
4. Verify password
A1: Not valid logon
A2: Wrong password
A3: ...

## 执行 Include
- 到达插入点时执行包含用例

## 什么是 Extend 关系？
- 从基本用例到扩展用例的联接
- 将扩展用例的行为插入基本用例
- 只有当扩展条件为真时才进行插入
- 在一个命令的扩展点插入基本用例

## Extend 关系示例

## 软件工程
## Extend 关系示例(续)
Get Quote Use Case
Basic Flow:
1. Include "Identify Customer" to verify customer identity.
2. Display options.
3. Customer selects "Get Quote".
4. Customer gets quote.
5. Customer gets other quotes.
6. Customer logs off.
A1. Quote System unavailable
Extension Points:
The "Optional Services" extension point occurs at Step 3 in the Basic Flow.

Get News Use Case
This use case extends the Get Quote Use Case, at extension point "Optional Services".
Basic Flow:
1. If Customer selects "Get News", the system asks customer for time period and number of news items.
2. Customer enters time period and log of items. The system sends stock trading symbol to News System, receives reply, and displays the news to the customer.
3. The Get Quote Use Case continues.
A1: News System Unavailable
A2: No News About This Stock

## 面向对象分析
## 执行 Extend
- 当到达扩展点并且扩展条件为真时执行
![](img/bd1e40ee9d51e0bf88db831d8e65a09d_56_0.png)

## 什么是 Use-Case Generalization?
- 从子用例到父用例的关系
- 在父用例中描述通用的共享的行为
- 在子用例中描述特殊的行为
- 共享共同的目标
![](img/bd1e40ee9d51e0bf88db831d8e65a09d_56_1.png)

## Generalization 示例
![](img/bd1e40ee9d51e0bf88db831d8e65a09d_56_2.png)

## Generalization 关系示例
Execute Trade Use Case
Basic Flow:
1. Customer Logs On
Include "Identify Customer" to verify customer identity.
2. Customer Selects "Trade".
Customer chooses trade...
3. Customer Selects Account
System displays account...
Perform Trade
4. Customer Begins New Trade
If customer wants other trades, repeat from Step 3...
6. Display Summary
System displays summary...
A1. Account Not Operational...

Execute Securities Trade Use Case
This use case is a child of the Execute Trade Use Case.
Trade Use Case.
Basic Flow:
1. Customer Logs On
2. Customer Selects "Trade"
3. Customer Selects Account
4. Perform Trade
If customer selects trade order type. The system performs... Limit Sell, Limit Buy...
The system sends...
5. Customer Begins New Trade
6. Display Summary
A1: Limit Sell Order...

## 什么是 Actor Generalization?
- Actors 可能有公共的属性
- 多个 actors 和 Use-Case 交互时可能有公共的角色或其的
![](img/bd1e40ee9d51e0bf88db831d8e65a09d_56_3.png)
4.2 - 11

## 软件工程
## Actor Generalization 示例
- Parent: Medical Worker
  - Medical Worker can read charts
- Children: Doctor, Nurse, Aide
  - Doctor, Nurse, and Aide can read charts

## 面向对象分析
## 面向对象分析
- 面向对象方法概述
- 面向对象的基本概念
- 用例建模
- 建立概念模型
- 用例分析

参考阅读：UML与C++的关系 UML与Java的关系 UML与VB的关系

## 面向对象分析的步骤
- 1. 用例建模
- 2. 建立概念模型
  - 2.1 识别 Conceptual Class
  - 2.2 建立 Conceptual Class 之间的关系
  - 2.3 增加 Conceptual Class 的属性
- 3. 用例分析

## 概念类图的作用
- When modeling the static view of a system, class diagrams are typically used in one of three ways, to model:
  - The vocabulary of a system
  - Collaborations
  - A logical database schema

## 面向对象分析的步骤
- 1. 用例建模
- 2. 建立概念模型
  - 2.1 识别 Conceptual Class
  - 2.2 建立 Conceptual Class 之间的关系
  - 2.3 增加 Conceptual Class 的属性
- 3. 用例分析

## Identify Conceptual Class
- Strategies to Identify Conceptual Classes
  - Use a conceptual class category list
  - Finding conceptual classes with Noun Phrase
  - Use analysis patterns, which are existing conceptual models created by experts
  - using published resources such as Analysis Patterns [Fowler96] and Data Model Patterns [Hay96].

