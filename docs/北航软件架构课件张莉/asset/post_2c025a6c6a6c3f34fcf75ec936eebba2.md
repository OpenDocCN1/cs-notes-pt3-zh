
## SADComponent

`<<SADComponent>>`的语义元模型

`<<SADComponent>>`示意图

## SADConnector

`<<SADConnector>>`的语义元模型

`<<SADConnector>>`示意图

Connector

- `<<delegation>>`: 将构件的外部端口连接到其内部提供契约实现的部分部件。
- `<<assembly>>`: 定义一个总体的接口端口与一个或多个接口端口之间的绑定关系。

properties

- isAbstract = false
- isActive = true
- multithread = true
- max_connect = 10

properties

- isAbstract = false
- Throughput = 10kbs

## 如何采用UML进行软件体系结构设计

### SAD Profile中构架配置的描述

![](img/da691714eec1b93795825838a75ee408_268_0.png)

## 如何采用UML进行软件体系结构设计

### SAD 约束规则

- 1) 每个`<<SADComponent>>`至少有一个端口，每个端口至少与一个接口相关联；
- 2) 端口不能独立被创建，只能在拥有该端口的构件被创建之后才能创建，并随构件的删除而被删除；
- 3) 角色不能独立被创建，只能在拥有该角色的连接件被创建之后才能创建，并随连接件的删除而被删除；
- ......
- 9) 角色绑定只能用于连接构件的端口和连接件的角色；
- 10) 如果构件的端口与连接件的角色通过角色绑定来连接，则构件的端口必须提供或要求角色所要求或提供的接口；
- 11) 接口定义了一组操作，构件不能直接被实例化；

## HPSM Profile

![](img/da691714eec1b93795825838a75ee408_269_0.png)

### HPSM Profile约束

- 1. `<<EJBSessionBean>>` 必须实现 `java.ejb.SessionBean` 接口；
- 2. 每个 `<<EJBSessionBean>>` 必须至少实现一个 `<<EJBCreateMethod>>`；
- 3. `<<EJBFinderMethod>>` 返回参数的类型必须是一个代表 EJB 接口的模型元素或是一个 Java Collection 类型的元素；
- ……
- 7. `<<EJBHomeInterface>>` 中所有的方法必须是 `<<EJBHomeMethod>>`；
- 8. 一个 `<<EJBHomeInterface>>` 与实现该接口的 EJB …

## PDL Profile

PDL Profile中定义了一组用于对模式进行定义和表示的建模概念

![](img/da691714eec1b93795825838a75ee408_270_0.png)

一个模式由一组角色及这些角色在结构和行为上的约束关系组成。

每个角色代表模式的一个重要特征，如拥有的构件、连接、接口、操作、属性等。

模式被实例化时，模式角色将被实际的构件、连接、接口、操作、属性等所代替。

`<<RelationConstraint>>`定义在模式实例化时扮演相应角色的实际模型元素之间必须具有的关系

## MAP Profile

- MAP Profile中定义了对不同层次模型间细化关系进行描述的语言元素

![](img/da691714eec1b93795825838a75ee408_270_1.png)

![](img/da691714eec1b93795825838a75ee408_270_2.png)

## 各Profile中的主要建模概念

| profile 核心概念 | SAS | SAD | HPSM | PDL | MAP |
|---|---|---|---|---|---|
| 构件 | `<<SASComponent>>` | `<<SADComponent>>` | `<<EJBEnterpriseBean>>`<br>`<<EJBEntityBean>>`<br>`<<EJBMessageDrivenBean>>`<br>`<<EJBSessionBean>>` | `<<PatternTemplate>>`<br>`<<PatternRole>>`<br>`<<ComponentRole>>`<br>`<<ConnectorRole>>`<br>`<<PortRole>>`<br>`<<InterfaceRole>>`<br>`<<AttributeRole>>`<br>`<<OperationRole>>`<br>`<<RelationConstraint>>`<br>`<<PatternInteraction>>`<br>`<<LifetimeRole>>` | `<<RefinementMapping>>`<br>具体映射类型包括<br>{decomposition, sharedFunction, concretization, detailing, dangling, Orphan} |
| 连接件 | `<<Control-Flow>>`<br>`<<Data-flow>>`<br>InformationFlow<br>Association<br>Dependency<br>Usage<br>`<<call>>`<br>`<<RPC>>`<br>`<<MessagePassing>>` | `<<SADConnector>>`<br>Connector {assembly, delegation}<br>`<<RoleBinding>>` | `<<RMI>>`<br>`<<call>>` |  |  |
|  |  | Interface | `<<EJBEntityHomeInterface>>` |  |  |

## 5 软件构架建模支持工具ArchME

- 软件构架建模支持工具的设计需求
- 软件构架建模环境ArchME功能概述
- ArchME的设计和实现方案

## 软件构架建模支持工具的设计需求

### 软件构架模型的表达能力

> 能为软件构架模型的表达提供有效的建模符号
> - 应简单、易掌握、支持软件构架由抽象到具体、由粗略到详细的逐步演化
> - 最好是可视化的
> 建模语言的选择是建模工具设计中必须考虑的重要问题之一

### 不同层次设计结果的衔接

> 下层模型通常在上层模型的基础上得到
> 应提供由上层模型快速获得下层模型初始结构的机制

### 软件构架建模支持工具的设计需求（续）

### 为设计人员提供辅助决策的必要手段

帮助设计人员搜寻和产生明智的决策，增加设计决策的效率和质量

### 模型检查和分析能力

> 保证模型语法上的正确性、一致性和完备性

### 工具易用性方面的考虑

> 模型创建：减少用户因频繁地进行鼠标移动而分散设计精力的可能性
> 排版支持：允许用户以相对比较随意的方式创建模型元素
> 信息过滤：允许用户根据需要选择显示或隐藏

## MAP Profile

MAP Profile中定义了对不同层次模型间细化关系进行描述的语言元素

![](img/da691714eec1b93795825838a75ee408_274_0.png)

### MAP Profile元模型

![](img/da691714eec1b93795825838a75ee408_274_1.png)

## 各Profile中的主要建模概念

| profile核心概念 | SAS | SAD | HPSM | PDL | MAP |
|---|---|---|---|---|---|
| 构件 | `<<SASComponent>>` | `<<SADComponent>>` | `<<EJBEnterpriseBean>>`、`<<EJBEntityBean>>`、`<<EJBMessageDrivenBean>>`、`<<EJBSessionBean>>` | `<<PatternTemplate>>`、`<<PatternRole>>`、`<<ComponentRole>>`、`<<ConnectorRole>>`、`<<PortRole>>`、`<<InterfaceRole>>`、`<<AttributeRole>>`、`<<OperationRole>>`、`<<RelationConstraint>>`、`<<PatternInteraction>>` | `<<RefinementMapping>>`，具体映射类型包括：`decomposition`、`sharedFunction`、`concretization`、`detailing`、`Orphan` |
| 连接件 | `<<ControlFlow>>`、`<<Data-flow>>`、InformationFlow、Association、Dependency、Usage、`<<call>>`、`<<RPC>>`、`<<MessagePassing>>` | `<<SADConnector>>`、Connector、{assembly, delegation}、`<<RoleBinding>>` | `<<RMI>>`、`<<call>>` | 连接件相关角色及约束 | — |
