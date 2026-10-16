
## RATIONAL USER CONFERENCE 2001

## MOF是自描述的

自描述
Domain-independant
Domain-specific
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

## RATIONAL USER CONFERENCE 2001

## MOF2.6.1

![](img/da691714eec1b93795825838a75ee408_308_0.png)

Figure 7-1 - MOF imports from the UML Core

## 包的Import与merge

- **Import**：使被导入包所包含的模型元素在导入包中可见和可使用
- **Merge**：合并包对被合并包中的模型元素进行扩展，可以增加新特征或者对原有特征进行细化

和UML中的定义一致，
在MOF中用于管理、重用、构建新的包

## RATIONAL USER CONFERENCE 2001

![](img/da691714eec1b93795825838a75ee408_309_0.png)

## MOF2.0

- MOF2.0中导入UML2.0基础设施中的核心包，实现UML2.0核心包的复用
- MOF2.0由Essential MOF（EMOF）和Complete MOF（CMOF）两个包组成
- EMOF和CMOF使不同复杂程度的元模型建模构造组织到不同包中，从而提升MOF建模元素的复用程度

## RATIONAL USER CONFERENCE 2001

![](img/da691714eec1b93795825838a75ee408_310_0.png)

## EMOF

- ◆ EMOF是MOF的核心，EMOF提供一些简单的
- 基本概念
- ◆ The EMOF model provides the minimal set of elements required to model object-oriented systems. EMOF reuses the Basic package from UML 2.0 Infrastructure Library as is for metamodel structure without any extensions, although it does introduce some constraint.

## RATIONAL USER CONFERENCE 2001

## 2.0

## MOF 2.5.1

Figure 12.1- EMOF Model - Overview

## RATIONAL USER CONFERENCE 2001

- **Reflection**: extends a model with the ability to be self describing.
- **Identifiers**: Provides an extension for uniquely identifying metamodel objects without relying on model data that may be subject to change.
- **Extension**: A simple means for extending model elements with name/value pairs.

## EMOF classes

![](img/da691714eec1b93795825838a75ee408_312_0.png)

## RATIONAL USER CONFERENCE 2001

![](img/da691714eec1b93795825838a75ee408_313_0.png)

![](img/da691714eec1b93795825838a75ee408_313_1.png)

## RATIONAL USER CONFERENCE 2001

## EMOF Types

![](img/da691714eec1b93795825838a75ee408_314_0.png)

## CMOF

- 通过扩展import或者merge扩展，EMOF可以扩展为CMOF
- CMOF为定义复杂元模型提供支持
- EMOF,CMOF,UML2.0均由CMOF中的建模元素定义

## RATIONAL USER CONFERENCE 2001

Figure 13.1 - CMOF Reflection

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

Figure 14.3 - CMOF Extension Packages

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

## RATIONAL USER CONFERENCE 2001

## The Complete MOF (CMOF) Model

![](img/da691714eec1b93795825838a75ee408_316_0.png)

Figure 14.1 - CMOF Packages

## MOF2.5.1

![](img/da691714eec1b93795825838a75ee408_316_1.png)

Figure 9.1 - The Reflection Package

## RATIONAL USER CONFERENCE 2001

## MOF2.5.1

Figure 12.2 - EMOF Classes

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

Figure 10.1 - The Identifiers package
