
- `setUp()`是建立测试环境，创建一个Hello类的实例；`tearDown()`用于清理资源，如打开的文件等等。以`test`开头的方法被认为是测试方法，JUnit会依次执行`testXxx()`方法。在`testAbs()`方法中，我们对`abs()`的测试分别择正数，负数和0，如果方法返回值与期待结果相同，则`assertEquals`不会产生异常。
- 如果有多个`testXxx`方法，JUnit会创建多个`XxxTest`实例，每次运行一个`testXxx`方法，`setUp()`和`tearDown()`会在`testXxx`前后被调用，因此，不要在一个`testA()`中依赖`testB()`。

直接运行 Run->Run As->JUnit Test，就可以看到JUnit测试结果；绿色表示测试通过，只要有1个测试未通过，就会显示红色并列出未通过测试的方法。可以试图改变 abs() 的代码，故意返回错误的结果（比如 return n+1;），然后再运行JUnit就会报告错误。

![](img/8454895dcf92bedbe5b40d0487077d64_183_0.png)

JUnit 单元测试，能在开发一段就找出许多 Bug，并且，多个 Test Case 可以组合成 Test Suite，让整个测试自动完成，尤其合于 XP 方法。每增加一个小的新功能或者对代码行了小的修改，就立刻运行一 Test Suite，确保新增和修改的代码不会破坏原有的功能，大大增强软件的可维护性，免代码渐“腐烂”。

## 示例
- 1. 建立hello（）类
- 2. 建立abs()方法；
- 3. 建立单元测试 Test Case——helloTest（）
- 4. 建立另一个math（）类
- 5. 建立add（）和 times（）方法
- 6. 建立单元测试 Test Case——mathTest（）
- 7. 建立测试 Test Suite

## 4.4 EMMA
- 测试覆盖率（Code Coverage）
- 测试覆盖率，简单的说，就是评价测试活动覆盖产品代码的指标。测试的目的，是确认产品代码按照预期一样工作，也可以看作是产品代码工作方式的说明文档。进一步考虑，测试覆盖率可以看作是产品代码质量的间接指标——之所以说是间接指标，因为测试覆盖率评价的是测试代码的质量，并不是产品代码的质量。
- 代码覆盖率是一种白盒测试，因为测试覆盖率是评价产品代码类内的指标，而不是评价系统接口或规约。测试覆盖率尤其用于评价测试代码是否已经覆盖了产品代码所有的路径。

## EMMA
- EMMA 是一种用来衡量 java 软件覆盖率的工具。它对于不可达代码的检测，以及验证测试和交互式测试对程序的覆盖情况是很必要的。
- EMMA的设计目标有以下几个，
- 1. 在不增加创建或执行开销的情况下，提供丰富的覆盖分析数据；
- 2. 促进困难开发展效率，同时，也能加快单元开发—测试周期；
- 3. 促进小型java软件的开发效率，同时，提高包含大类的的大型企业软件的开发。
- EMMA与其他覆盖测试工具的区别在于它面向极简编程，目的是促使循环的开发—测试软件开发模型。

- 衡量测试覆盖率的指标很多，常用的指标有：
- **Statement coverage**，也称作Line coverage，用于评价测试的代码语句覆盖率。
- **Basic block coverage**，是Statement coverage的一个变种，它把没有一个分支的代码区域作为一个计算单位，而不是简单的代码行，用于一个if-else分支代码行数大于另一个的情况，在这种情况下，statement coverage指标并不适用。
- **Decision coverage**（也称作Branch coverage），用于评价代码分支的测试覆盖率。
- **Path coverage**，和Decision coverage相似，用于评价代码从开始到结束所有路径的测试覆盖率。
- **Function coverage**，用于评价代码方法的测试覆盖率。
- **EMMA目前支持四种Coverage类型：**
  - class、method、line和basic block。

## 安装EclEmma插件
- EclEmma是一个基于EMMA的Java代码覆盖工具。它的目的是让你可以在Eclipse工作平台中使用强大的Java代码覆盖工具EMMA。EclEmma是非侵入式的不要修改你的项目或执行其它任何安装，它能够在工作平台中启动像运行JUnit测试一样直接对代码覆盖进行分析。
- 安装 EclEmma 插件的流程和大部分Eclipse 插件相同，既可以 Eclipse 标准的 Update 机制来进行安装 EclEmma 插件，也可以从站点下 zip 文件并解压到 eclipse 所在的目录中。

## 安装 EclEmma 插件
Eclipse的标准 Update 机制流程安装 EclEmma 插件

添加 EclEmma 更新站点
- Help →Install New Software... →Add

![](img/8454895dcf92bedbe5b40d0487077d64_190_0.png)
- Name: EclEmma
- URL: http://update.ecllemma.org/

## Available Software
Check the items that you wish to install.

Work with: Eclemma - http://update.eclemma.org/

Add...

Find more software by working with the "Available Software Sites" preferences.

type filter text

| Name | Version |
|------|---------|
| ☑ EclEmma |  |

Select All

Deselect All

1 item selected

Details

☑ Show only the latest versions of available software

☑ Group items by category

☐ Show only software applicable to target environment

☑ Contact all update sites during install to find required software

☑ Hide items that are already installed

What is already installed?

< Back

Next >

Finish

Cancel

## 使用EclEmma 进行测试覆盖率
示例：
- 利用EclEmma测试程序行覆盖率
- 生成EclEmma测试JUnit覆盖率报告
- 导出EclEmma覆盖率报告

## 4.5 实例
## XXXX支撑软件与可视化软件
## 测试计划

## 目录
- 1、简介
- 1.1 编写目的
- 1.2 背景
- 1.3 测试范围
- 1.4 参考文档
- 2、测试参考文档和测试提交文档
- 2.1 测试参考文档
- 2.2 测试提交文档
- 3、测试策略
- 4、测试资源
- 4.1 人力资源
- 4.2 测试环境
- 4.3 测试工具
- 5、测试策略

- 5.1功能测试
- 5.1.1 XXX系统管理软件功能测试
- 5.1.2 XXX系统实时通信软件功能测试
- 5.1.3目标三维动态显示模型及可视化软件功能测试
- 5.1.4XXX三维动态显示模型及可视化软件功能测试
- 5.1.5 XXX交会显示软件功能测试
- 5.1.6XXX系统数据管理软件功能测试
- 5.1.7 XXX文件与AutoCAD、Creator的转换软件功能测试
- 5.2性能测试
- 5.2.1 讯性能测试
- 5.2.2 实时性能测试
- 5.2.3 数据库性能测试
- 5.2.4 显示性能测试
- 5.2.5 其它性能测试
- 5.3故障测试
- 5.3.1网络故障
- 5.3.2 服务器故障
- 5.3.3 管理计算机故障
- 5.3.4 计算节点机故障
- 5.3.5 图形工作站故障测试
- 5.4安全性测试
- 5.4.1管理软件安全性测试
- 5.4.2 数据管理软件安全性测试

## # 1、简介
## ## 1.1 编写目的
为了全面、系统地对“XXX支撑软件与可视化软件”进行评估与测试，从而保证系统期望稳定的运行，组织对该软件进行系统的总体综合测试。

## ## 1.2 项目背景
“XXX证评平台”是中国兵器工业XXX研究所承担的国防基础科研项目。XXX所与XXX大学合作，对该项目的关键技术——XXX支撑技术和可视化技术开展研究。本项目就是在此背景下开展的，主要应用虚拟试验技术、计算机网络技术、可视化技术、数据库技术等，研制“XXX的支撑软件和可视化软件”，并最终集成在“XXX中”。

本软件系统由以下7个二级软件组成：
- 系统管理、实时通讯、三维显示、……
