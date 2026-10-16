

## AADL的产生

- 1991年Honeywell实验室基于嵌入式系统提出了MetaH语言
- 2001年美国汽车电子协会SAE提出了航空架构描述语言AADL（Avionics Architecture Description Language），由于以上两个语言不足以解决现实中航空系统存在的一些问题。
- 2004年SAE，卡内基梅隆大学CMU和Honeywell实验室在MetaH和AADL的基础上提出了架构分析和设计语言AADL（Architecture Analysis and Design Language）。
- 在2004年推出基于Eclipse Osate的1.0版本《Open Source AADL Tool Environment》，
- 2009年推出Osate2.0版本。

## AADL介绍

- AADL标准定义了三种模型描述的方式：文本化，XML和图形化。正是由于这种多样化的描述方式，AADL可以被许多不同的工具所使用。对UML的支持同样允许我们在UML的工具中插入AADL。
- 作为一种体系结构描述语言，AADL通过描写构件和连接来建立系统的体系结构。一个AADL的描述由一系列构件的描述组成，通过对这种描述的实例化来建立系统体系结构的模型。

## AADL描述方式（文本化、XML、图形化）

![](img/da691714eec1b93795825838a75ee408_214_0.png)

## AADL的构件

- AADL的构件的定义包括两部分：构件的类型和构件的实现。一个AADL的构件拥有一个类型（component type）以及对应的零个、一个或者很多个实现（component implementation）。
- 构件的类型描述了对外的功能接口（进出端口，属性等）。
- 构件的实现描述了构件的内部结构（子构件，其他的属性等）。
- 一个构件的类型可以有多个实现，和构件类型一样，一个实现同样可以扩展为其他的实现。

## AADL构件的种类

- AADL定义了很多构件的种类，总的来说可以分成三大类：**软件构件、执行平台构建以及组合构件**。
- **软件构件**用于软件体系结构建模，包括数据(data)、线程(thread)、线程组(thread group)、进程(process)、子程序(subprogram)构件。
- **执行平台构件**用于硬件体系结构建模，包括处理器(processor)、存储器(memory)、总线(bus)、外设(device)构件。
- **系统构件**组合所有的构件，层次化地建立系统的体系结构。

![](img/da691714eec1b93795825838a75ee408_215_0.png)

## AADL构件的描述

![](img/da691714eec1b93795825838a75ee408_215_1.png)

## AADL 的特点

- AADL 支持文本和图
- AADL可以用来描述系统的体系结构，以及输入输出）和性能关
- AADL可以用来描述输入数据和代码构建，Memory可以在... process内，也可以在...
- AADL...平台构建，通过总线和...运行体系结构的动态行为。

```
memory RAM
features
port requires bus access membus.hbus;
end RAM;

memory implementation RAM.comp.RAM
subcomponents
SRAM01: memory XRAM.1ERAM;
XRAM01: memory XRAM.1SRAM;
end RAM.comp.RAM;

memory XRAM
...

memory implementation XRAM.1SRAM
...

memory implementation XRAM.1SRAM
...

bus membus
...

bus implementation membus.hbus
...
```

![](img/da691714eec1b93795825838a75ee408_216_0.png)

## AADL研究现状

- AADL语言的研究
- AADL建模方法的研究
- AADL模型转换
- AADL模型转换
- AADL模型的验证与分析
- 基于AADL模型的自动代码生成

## AADI应用实践：

- **TOPCASED**：TOPCASED由空中客车公司（空客）提出并应用的项目，采用模型驱动开发和形式化验证相结合、多种开源工具集成的思想，支持复杂嵌入式实时系统的设计、开发与实现，以保证系统的质量属性并降低开发时间和成本。
- **COTRE**：COTRE是空中客车公司的一个项目，它的目标是在软件设计到实现的工业过程中，将形式化方法和半形式化方法相结合，定义一种实用的、工具性的建模和验证方法，并且将这种方法应用到实际生产中。
- **ASSERT**：ASSERT项目的目标是对嵌入式实时系统的开发过程的改进。AADL被用来描述所开发系统的体系结构，由于它的良好扩展性，可以用于支持那些必要的信息，特别是基于验证机制的工业系统的特别数据（验证的描述，非功能性要求，条件的可行性等等）。

## XYZ/ADL

- XYZ/ADL是中国科学院软件工程研究所唐稚松院士等定义的一种基于时序逻辑的软件体系结构描述语言。
- XYZ/ADL以时序逻辑语言XYZ/E为形式化基础，可以在统一的时序逻辑框架下描述系统静、动态语义结构，并可进行相关性质分析。
- 有一套基于XYZ/E的CASE工具集作为底层支撑，可对软件体系结构进行描述、分析、求精、验证，直至最终系统的编译实现。

## XYZ/ADL

- 特点：
  - 支持层次设计软件体系结构，设计过程从外到内部的不断求精过程。
  - 是可视化的体系结构描述语言，支持软件系统的体系结构设计。
  - 在体系结构的每步设计中，XYZ/ADL能生成相应的XYZ/ADL程序。

- XYZ/ADL的基本概念有：组件、连接件、系统、端口、角色、性质、配置、体系结构和风格，以及粘接操作和绑定操作。其中组件、连接件和系统是最主要的实体元素。
  - 组件是一个具有一定功能的逻辑单元或者存储对象。典型组件的例子有：客户机，服务器，过滤器，对象，黑板，数据库等。组件由接口和内部规范组成。
  - 组件的接口包括一组端口和一个性质描述。
  - 连接件用作定义组件之间的交互方式和规则。
  - 连接件由接口和交互协议组成。

## XYZ/ADL

组件和连接件是体系结构的基本元素，它们的构成如图所示。

![](img/da691714eec1b93795825838a75ee408_218_0.png)

## XYZ/ADL

XYZ/ADL
中体系结构
概念之间关
系直观地表
示如图。

![](img/da691714eec1b93795825838a75ee408_219_0.png)

## XYZ/ADL

- 规定图形方式作为我们的体系结构框图表示。

![](img/da691714eec1b93795825838a75ee408_219_1.png)

- 例如：假设过滤器组件Filter1用来计算输入数的阶乘。有一个数据输入端口DataIn输入整数，和一个数据输出端口DataOut输出结果，那么Filter1可描述如下：

```
%COMPONENT Filter1=[
%PORT DataIn=INT;
□ [LB₁= START⇒$0DataIn?x ∧$0LB₁=L1;
LB₁= L1 ∧ ¬ (x=EOF ) ⇒$0DataIn?x ∧$0LB₁=L1;
LB₁=L1 ∧ (x=EOF) ⇒$0LB₁=STOP
]
```

```
%PORT DataOut==INT;
□ [LB₂=START⇒$0LB₂=L1;
LB₂= L1 ∧ ¬ (y=EOF ) ⇒$0DataOut?y ∧$0LB₂=L1;
LB₂= L1 ∧ ¬ (y=EOF ) ⇒$0DataOut!EOF ∧$0LB₂=STOP
]
%PROPERTY==□ [ (x>0⇒∃(y=x!)) ∧~DataOut!y ]
%COMPUTATION==
□ [LB=START ⇒$0x=0∧$0y=0∧$0LB=L0;
LB=L0⇒$0DataIn?x∧$0LB=L1;
LB=L1∧(x=EOF ) ⇒$0LB=L2;
LB=L1∧(x=EOF ) ⇒$0LB=End;
LB=L2∧¬(x<0) ⇒∃(y=x! ∧LB=L3);
LB=L2∧(x<0) ⇒$0LB=L0;
LB=L3⇒$0DataOut!y∧$0LB=L0;
LB=End⇒$0DataOut!EOF∧$0LB=STOP
]
```

- 例如，组件Filter1的内部规范可以是上述的较抽象描述，也可以是具体的算法描述：

```
%COMPUTATION=
□ [LB =START ⇒ $OLB=L0;
LB=L0⇒ $0DataIn?x ∧ $OLB=L1;
LB=L1 ∧ ¬(x=EOF) ⇒ $OLB=L2;
LB=L1 ∧ (x=EOF) ⇒ $OLB=End;
LB=L2 ∧ ¬(x<0) ⇒ $Oi=1 ∧ $Oy=1 ∧ $OLB=L3;
LB=L2 ∧ (x<0) ⇒ $OLB=L0;
LB=L3 ∧ (i<x) ⇒ $Oy=y*i ∧ $Oi=i+1 ∧ $OLB=L3;
LB=L3 ∧ ¬(i<x) ⇒ $0DataOut!y ∧ $OLB=L0;
LB=End⇒DataOut!EOF ∧ $OLB=STOP
]
```

## ADL的发展方向

- 除此之外，还有北京大学信息科学技术学院梅宏等人提出的支持构件组装的描述语言ABC/ADL，中国东北大学软件中心定义的专门用于多智能体系统的描述语言A-ADL (Agent-Based -ADL) 等。

- 现状:

  - 当前ADL研究主要侧重于对软件体系结构分析、演化、以及代码自动生成能力的研究。
  - 每种ADL分别侧重软件体系结构设计的某些方面，适于解决不同的问题。
  - 在软件体系结构研究初期，这种“百家争鸣”的情况为人们深入理解软件体系结构不同方面的特性，以及软件体系结构设计在开发过程中的作用有积极的意义。但随着软件体系结构技术的不断发展，尤其是经历了对基本概念的收集、整理阶段，逐渐向实际项目开发中推广和应用时，这种情况长时间维持下去，将不利于软件体系结构设计工具的研发和软件体系结构技术的推广。

