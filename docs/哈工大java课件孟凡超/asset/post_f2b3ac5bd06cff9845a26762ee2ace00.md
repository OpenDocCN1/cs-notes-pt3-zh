
## Java程序设计

孟凡超

哈尔滨工业大学(威海)计算机科学与技术学院

mfc@hitwh.edu.cn

## 参考资料

- 1. 辛运帏, 饶一梅, 马素霞. Java程序设计(第二版). 清华大学出版社, 2006.

## 课程安排

- 讲课24学时，占总成绩60%。
- 实验16学时，占总成绩40%。
- 实验课地点研究院楼中405，406，时间第5周和第7周的周2和周5的晚上。

## 课程内容

- 概述
- 标识符和数据类型
- 表达式和流程控制语句
- 数组、向量和字符串
- 进一步讨论对象和类
- Java语言中的异常
- Java的图形用户界面设计
- Swing组件
- Java Applet
- Java数据流
- 线程

## 第1章 概述

- 什么是Java语言
- JDK的下载、安装和配置
- 一个基本的Java应用程序
- 使用Eclipse开发Java应用程序

## 什么是Java语言

### Java语言的起源与发展历程

1991年4月，Sun Microsystem公司(已被甲骨文公司收购)的James Gosling领导了一个称为Green的项目组，其目的是为在电视、烤箱等家用消费类产品上进行交互式操作而开发一个名为Oak的语言。

![](img/ca8bdf2cb3b7905fc97ee695aef3ed57_5_0.png)

![](img/ca8bdf2cb3b7905fc97ee695aef3ed57_5_1.png)

- 1992年，Oak的第一个成果是可触摸控制的手持家庭娱乐设备控制器，名为star seven(*7)。Sun公司为Green项目成立First Person公司。
- 1993年，First Person公司重定位Oak，转向网络应用领域。(背景：WWW开始席卷全球，静态网页)
- 1994年，Oak技术包括源代码全部免费公开。Oak开发出网络浏览器Webrunner(后更名为Hot Java)。Oak编写的Applet网页由静态转为动态。
- 1995年，Oak注册登记时，发现该名已被占用，因此，更名为Java。First Person公司解散。Java当年被评为十大优秀科技产品之一。JDK1.0 α2版本正式对外发布。

### 什么是Java语言

### Java为何称为Java？

项目组骨干人员在咖啡馆品尝热腾腾、香浓的Java（爪哇岛特产）咖啡而产生的灵感。

![](img/ca8bdf2cb3b7905fc97ee695aef3ed57_7_0.png)

- **1996年**，Sun 成立Javasoft公司来发展Java。Netscape支持Java，IBM、Symantec、Inprise、Microsoft IE支持Java，众多第三方的Java编译器被推出，例如VJ++、JBuilder等。
- **1997年**，JDK1.1（Java Development Kit）发布。
- **1998年**，JDK1.2发布，JDK更名为J2SDK（Java 2 Software Development Kit），J2SDK1.2又名Java 2，并将Java的应用细分（企业版J2EE、标准版J2SE和微型版J2ME）。
- **2000年5月8日**，JDK1.3发布；**2000年5月29日**，JDK1.4发布；**2001年9月**，J2EE1.3发布；**2002年2月**，J2SE1.4发布。

- > 2004年9月，J2SE1.5发布，为了表示该版本重要性，J2SE1.5更名为Java SE5.0。
- > 2005年6月，Java SE6发布，此时，Java的各种版本已经更名，以取消其中的数字“2”，J2EE→Jave EE，J2SE→Java SE，J2ME→Java ME。
- > 2006年12月，Sun公司发布JRE6.0。
- > 2009年4月，甲骨文收购Sun，取得Java版权。
- > 2011年7月，甲骨文发布Java7.0的正式版。
- > ……

![](img/ca8bdf2cb3b7905fc97ee695aef3ed57_8_0.png)

### Java语言

- 面向对象的程序设计语言
- 与机器无关的二进制格式的类文件
- Java虚拟机(用来执行类文件)
- 完整的软件包(跨平台的API和库)

### Java语言的优势---软件可移植性

Java应用程序可以在支持Java的任何系统上运行

Java编辑工具

Java源程序
(.java文件)

Java编译器

Java字节码
(.class文件)

二进制

Java运行时

Java虚拟机

Java虚拟机

Java虚拟机

Java虚拟机

Java虚拟机

移动电话PDA

Window系统

Linux系统

Macintosh系统

UNIX系统

### Java虚拟机

Java虚拟机(Java Virtual Machine, JVM)是在一台真正的机器上用软件方式实现一台假想机。JVM有自己想象中的硬件，如处理器、堆栈、寄存器等，还有相应的指令系统。

一个运行时的JVM实例的职责是：负责执行一个Java程序。当启动一个Java程序时，一个虚拟机实例也就诞生了，当该程序关闭退出后，这个虚拟机实例也就随之消亡。如果一台计算机上同时运行三个Java程序，将得到三个Java虚拟机实例，每个Java程序都运行于它自己的Java虚拟机实例中。

JVM实例和JVM执行引擎实例：JVM实例对应了一个独立运行的Java程序，它是进程级别；JVM执行引擎实例则对应了属于用户程序的线程，它是线程级别的。

### JVM的生命周期

- JVM实例的诞生。当启动一个Java程序时，一个JVM实例就产生了，任何一个拥有public static void main(String[] args)函数的class都可以作为JVM实例运行的起点。
- JVM实例的运行。main()作为该程序初始线程的起点，任何其它线程均由该线程启动。JVM内部有两种线程：守护线程和非守护线程，main()属于非守护线程，守护线程通常由JVM自己使用，Java程序也可以标明自己创建的线程是守护线程。
- JVM实例的消亡。当程序中的所有非守护线程都终止时，JVM才退出。若安全管理器允许，程序也可以使用Runtime类或者System.exit()来退出。

### JVM体系结构

class文件

类装载子系统

用来装载class文件

方法区

堆

Java栈

PC寄存器

本地方法栈

运行时数据区

执行引擎

本地方法接口

本地方法库

执行字节码或本地方法

### JVM体系结构-类加载器

JVM将整个类加载过程分为三步：

(1)装载：装载过程负责找到二进制字节码加载至JVM中，JVM通过类名、类所在的包名由ClassLoader来完成类的加载。因此，可以采用：类名+包名+ ClassLoader实例ID来标识一个被加载的类。

(2)链接：链接过程负责对二进制字节码的格式进行校验、初始化装载类中的静态变量以及解释类中调用的接口、类。

(3)初始化：初始化过程即为执行类中的静态初始化代码、构造器代码以及静态属性的初始化。在四种情况下初始化过程会被触发执行：调用new；反射调用了类中的方法；子类调用了初始化；JVM启动过程中指定的初始化。

✓JVM类加载器组织结构

![](img/ca8bdf2cb3b7905fc97ee695aef3ed57_15_0.png)

引导类加载器：这是JVM的根类加载器，它是用C++编写，JVM启动时初始化此类加载器，并由此类加载器完成$JAVA_HOME中jre/lib/rt.jar(JDK的实现)中所有class文件的加载，这个jar中包含了Java规范定义中的所有接口及实现。(加载Java核心库)

扩展类加载器：JVM用此类加载器来加载扩展功能的一些jar包。(加载Java扩展库)

系统类加载器：JVM用此类加载器来加载启动参数中指定的类路径(Classpath)中的jar包以及目录。一览来说，Java的应用类都是由它来加载的。

用户定义类加载器：是Java开发人员继承ClassLoader抽象类自行实现的类加载器，基于自定义的类加载器可以用于加载非类路径(Classpath)中的jar以及目录。

### Java平台的三种版本

- 微型版-J2ME(Java 2 Platform Micro Edition)/Java ME

Java ME是为机顶盒、移动电话和PDA之类的嵌入式消费电子设备提供的Java语言平台，包括虚拟机和一系列标准化的Java API。

与Java SE和Java EE相比，Java ME总体的运行环境和目标更加多样化，但是其中的每一种产品的用途却更为单一，而且资源限制也更加严格。

开发Java ME程序一般不需要特别的开发工具，开发者只需装上Java SDK及下载免费的Sun Java Wireless Toolkit 2.xx系列开发包，目前主要的集成开发环境IDE(如Eclipse、NetBeans)都支持Java ME的开发，个别手机开发商如Android系统，都有自己的SDK，供开发者再开发出兼容于他们平台的程序。

- 标准版-J2SE(Java 2 Platform Standard Edition)/Java SE

Java SE用于开发和部署桌面、服务器以及嵌入式设备和实时环境中的Java程序。Java SE包括用于开发Java Web服务的类库，同时Java SE为Java EE提供了基础。目前，Java程序设计课程使用的基本都是Java SE。
