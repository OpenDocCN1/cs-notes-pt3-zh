

## LoadRunner——基础知识

- LoadRunner的概念解析
- LoadRunner的工作原理
- LoadRunner的使用
  - 脚本录制与开发
  - 场景创建与执行
  - 测试结果分析

## LoadRunner——支持协议
### LoadRunner支持的协议

- **客户端/服务器：** MS SQL, ODBC, Oracle, DB2, Sybase, Sockets…
- **自定义：** C, Visual Basic, Java…
- **分布式组件：** COM/DCOM, CORBA, RMI
- **电子商务：** FTP, Palm, SOAP, Web…
- **ERP/CRM：** SAP, Oracle, PeopleSoft, Siebel…
- **邮件服务：** IMAP, MS Exchange, POP3, SMTP
- **无线：** WAP, VoiceXML…

![](img/88f667f5480db09ef600e4e177b09268_549_0.png)

## LoadRunner——架构
### LoadRunner架构

四个组成部分：

- 1. **虚拟用户发生器（Vuser Generator，VuGen）**：捕获业务流程和创建自动化测试脚本，即自动生成大部分测试脚本。
- 2. **压力调度和监控中心（Controller）**：运行和监视测试脚本
- 3. **压力产生器（Load Generator）**：产生虚拟客户端的请求，用来在服务器上创建负载。
- 4. **压力结果分析工具（Analysis）**：集成数据统计分析功能，自动生成测试报告文档

## LoadRunner——工作原理
### LoadRunner 工作原理
### LoadRunner 如何工作

- 1. Controller 是一个中央控制台，用于管理和监控负载测试。
- 2. 成千上万的虚拟用户在系统上执行真实的事务，以模拟生产流量。
- 3. 实时监视器捕获跨所有层级、服务器和网络资源的性能数据，并在 Controller 上显示信息。
- 4. 结果存储在数据库仓库中，使用户能够生成报告并进行分析。

![](img/88f667f5480db09ef600e4e177b09268_552_0.png)

被测应用

LoadRunner 控制器

### LoadRunner内部结构

LoadRunner 测试工作流程 1-22

详见 LoadRunner 自带说明文档

## LoadRunner——测试步骤
### LoadRunner测试步骤

![](img/88f667f5480db09ef600e4e177b09268_555_0.png)

- 1. 制定性能测试计划
- 2. 录制并修改Vuser脚本（事务、参数化、关联）
- 3. 方案场景描述测试活动中发生的各种事件（集合点）
- 4. 运行场景并实时监测
- 5. 分析数据，生成性能评估报告

## LoadRunner——部署和安装

注意事项：

- 1. LoadRunner对浏览器的支持：
  - 8.x支持IE6，支持IE更高版本需要安装补丁FP4；
  - 9.x支持IE7-8、Firefox，但不稳定
- 2. 安装过程漫长，约20分钟
- 3. 练习中需要安装Samples
- 4. 安装目录不支持中文

![](img/88f667f5480db09ef600e4e177b09268_556_0.png)

Mercury LoadRunner 8.0

Mercury LoadRunner

更新 许可证 关于 支持 帮助 退出

负载测试 诊断 调优 新增功能

- 创建/编辑脚本
- 运行负载测试
- 分析负载测试

负载测试通过在新系统或升级部署之前检测瓶颈，避免生产环境中代价高昂且令人头疼的性能问题。通过在 QA 或预发布环境的 IT 系统上创建生产工作负载，您可以测量负载下关键业务流程的性能，并定位瓶颈以快速解决。Mercury Interactive 的 LoadRunner® 为最常见的协议和技术提供全面支持，包括 ERP/CRM、Web、J2EE、XML、.NET、无线和流媒体，使 IT 团队能够使用单一产品对所有企业应用进行负载和性能测试。使用 Mercury Interactive 的 LoadRunner® 实施有效的负载测试流程，有助于确保新应用或升级后的应用满足服务水平目标，并在部署到生产环境时不出现性能意外。

了解有关负载测试的更多信息

```c
vuser_init()
{
    lr_start_transaction("login");
    web_url("MercuryWebTours",
        "URL=http://localhost/MercuryWebTours/",
        "Resource=0",
        "RecContentType=text/html",
        "Referer=",
        "Snapshot=t6.inf",
        "Mode=HTML",
        LAST);
}
```

Vuser 已终止。

## LoadRunner——脚本录制与开发

- Virtual User Generator简介
- VuGen录制功能
- 修改Vuser脚本
  - 参数化
  - 集合点
  - 检查点
  - 关联
- 配置Vuser脚本

### Virtual User Generator简介

### VuGen录制原理

录制过程

![](img/88f667f5480db09ef600e4e177b09268_560_0.png)

运行过程

![](img/88f667f5480db09ef600e4e177b09268_560_1.png)

