

## 理性用户大会 2001

## MOF是自描述的

自描述
领域无关
领域特定
M3层
MOF
instance of
UPM元模型
UML元模型
CCM元模型
M2层
M1层
对象和数据
对象和数据
M0层

M3是谁的实例？层次止于此。MOF是自描述的。

仅在私边拷贝 www.mdasky.com

## 四层元模型体系结构

M0(Run-time instance)
aVidio

M1(user model)
Video
title: String
:Video
title = "2001: A Space Odyssey"
<<snapshot>>

M2(UML)
Attribute
Class
Instance
<<classifier>>
<<instance of>>

M3(MOF)
Class(MOF)
<<instance of>>

![](img/da691714eec1b93795825838a75ee408_305_0.png)

![](img/da691714eec1b93795825838a75ee408_305_1.png)

## MOF

- 什么是MOF？
- 什么是模型
- 四层元模型
- MOF的核心元建模构造
- MOF的应用（后面讲）

## MOF的演化

- 1997年，OMG制定了MOF1.1规范
- 自1997年开始，OMG对MOF1.1进行过较小的修订，2002年4月MOF1.4正式被采用
- 2006年发布MOF2.0正式版。
  - 内容有了很大的变化。
  - 受UML2.0的影响，与UML2.0共享核心包
  - 优点：
    - 简化元建模规则，统一建模概念（UML和MOF）
    - 更多的工具支持，基本上支持UML的工具都支持MOF建模

## 理性用户大会 2001

## MOF2.6.1

![](img/da691714eec1b93795825838a75ee408_308_0.png)

图 7-1 - MOF 从 UML 核心导入

## 包的Import与merge

- **Import**：使被导入包所包含的模型元素在导入包中可见和可使用
- **Merge**：合并包对被合并包中的模型元素进行扩展，可以增加新特征或者对原有特征进行细化

和UML中的定义一致，
在MOF中用于管理、重用、构建新的包

## 理性用户大会 2001

![](img/da691714eec1b93795825838a75ee408_309_0.png)

## MOF2.0

- MOF2.0中导入UML2.0基础设施中的核心包，实现UML2.0核心包的复用
- MOF2.0由Essential MOF（EMOF）和Complete MOF（CMOF）两个包组成
- EMOF和CMOF使不同复杂程度的元模型建模构造组织到不同包中，从而提升MOF建模元素的复用程度

## 理性用户大会 2001

![](img/da691714eec1b93795825838a75ee408_310_0.png)

## EMOF

- ◆ EMOF是MOF的核心，EMOF提供一些简单的
- 基本概念
- ◆ EMOF 模型提供了建模面向对象系统所需的最小元素集。EMOF 按原样重用 UML 2.0 基础设施库中的 Basic 包作为元模型结构且不做任何扩展，尽管它确实引入了一些约束。

## 理性用户大会 2001

## 2.0

## MOF 2.5.1

图 12.1- EMOF 模型 - 概览

## 理性用户大会 2001

- **Reflection**: 扩展模型使其具有自描述的能力。
- **Identifiers**: 提供一种扩展，用于在不依赖可能发生变化的模型数据的情况下唯一标识元模型对象。
- **Extension**: 通过名称/值对扩展模型元素的一种简单方法。

## EMOF 类

![](img/da691714eec1b93795825838a75ee408_312_0.png)

## 理性用户大会 2001

![](img/da691714eec1b93795825838a75ee408_313_0.png)

![](img/da691714eec1b93795825838a75ee408_313_1.png)

## 理性用户大会 2001

## EMOF 类型

![](img/da691714eec1b93795825838a75ee408_314_0.png)

## CMOF

- 通过扩展import或者merge扩展，EMOF可以扩展为CMOF
- CMOF为定义复杂元模型提供支持
- EMOF,CMOF,UML2.0均由CMOF中的建模元素定义

## 理性用户大会 2001

图 13.1 - CMOF 反射

PrimitiveTypes

<<import>>

Common
(from Logical View)

<<import>>

<<import>>

CMOFReflection
(from Logical View)

CMOFExtension

Element

Element
+element 0..*
+tag 0..*
Tag

图 14.3 - CMOF 扩展包

CMOF Reflection package

Classifier

Association
isDerived: Boolean = false

Property
isReadOnly: Boolean = false
isDerivedUnion: Boolean = false

Class
isAbstract: Boolean = false

Operation

## 理性用户大会 2001

## 完整的 MOF (CMOF) 模型

![](img/da691714eec1b93795825838a75ee408_316_0.png)

图 14.1 - CMOF 包

## MOF2.5.1

![](img/da691714eec1b93795825838a75ee408_316_1.png)

图 9.1 - 反射包

## 理性用户大会 2001

## MOF2.5.1

图 12.2 - EMOF 类

## MOF::Reflection::Object

get property : Property : Object(query)
=equals(element : Object) : Boolean(query)
+set property : Property, value : Object()
+isSet(property : Property) : Boolean(query)
+unset property : Property()
+invoke(op : Operation, arguments : Argument[0..*] ) : Object[0..1]

## MOF::Identifiers::Extent

+isContainment() : Boolean(query)
+elements() : ReflectiveSequence(query)

## MOF::Identifiers::URExtent

+content() : String(query)
+uri(object : Element) : String(query)
+element(uri : String) : Element(query)

## UML::Package

+URI : String[0..1]
+makeVisible(al : NamedElement) : Boolean(query)
+mustBeOwned() : Boolean(redefines mustBeOwned(query))
+nestPackage() : Package[0..*](query)
+ownedType() : Type[0..*](query)
+subElements() : PackagedElement[0..*](query)

## UML::Property

+isID : Boolean = false
+isAttribute() : String[0..1](query)
+hasAttribute(p : Property) : Boolean(query)
+isConsistentWith(redefines : RedefinableElement) : Boolean(redefines isConsistentWith(query))
+isNavigable() : Boolean(query)
+opposite() : Property(query)
+subSettingContext() : Type[0..*](query)

## ::PrimitiveTypes

## MOF::Common

## MOF::Identifiers

图 10.1 - 标识符包

