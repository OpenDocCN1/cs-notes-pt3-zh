
# 新设计引入
accept()方法

将TacCalculator 更改为 TaxVisitor类。将所有的 方法都改为访问方法。为 每个类单独设计一个访问 方法，以便获得相应的 Tax信息。

![](img/95717dc23f76db2057b9aa0c49790307_1061_0.png)

# Example 2: tax computation problem (税收问题)

# 新设计的解释

# In the improved design

- 1. 改进类名 Class name TacCalculator has been changed into TaxVisitor
- 2. 改进方法名 Method names in class TaxVisitor have been changed into the form visitxxx:
  > visitxxx means that this method is to get information from class xxx and calculate tax for class xxx.
- 3. 增加accept()方法。 In each subclass of class Tax, add a method named accept() to pull in a specific visit method.

# Example 2: tax computation problem (税收问题)

为什么要引入访问者方法与接受方法：

意图：利用 accept() 与 visit() 方法，在 Tax 层次类与 TaxVisitor 之间精心地设计一个接口，以便使得两个类能通过该接口连接起来，例如：

![](img/95717dc23f76db2057b9aa0c49790307_1063_0.png)

![](img/95717dc23f76db2057b9aa0c49790307_1063_1.png)

# Example 2: tax computation problem (税收问题)

怎样设计接口呢？

四人帮利用accept 方法建立两个类之间的接口。

![](img/95717dc23f76db2057b9aa0c49790307_1064_0.png)

# 类ElectronicTax 中的accept 方法

```
accept(TaxVisitor v)
    v. visitElectronicTax()
}
```

# Example 2: tax computation problem (税收问题)

两个对象是怎样被链接在一起的呢？

```
TaxVisitor v = new TaxVisitor();
Tax tax = new ElectronicTax();
tax.accept(v)
```

tax.accept(v); 使用accept方法，而不是通过构造方法将访问者对象拉入

Client
main()

ElectronicTax
+accept(Visitor v)
+getData:double

v.visitElectronicTax(this)

tax.getData()

v. visitElectronicTax()

TaxVisitor
+visitElectronicTax (ElectronicTax e){
e.getData();
}

Interactions involved in the above design

# Example 2: tax computation problem (税收问题)

:Client

tax.accept(v);

:ElectronicTax

visitElectronicTax(tax)

:TaxVisitor

Client 类负责创建两个类的对象并且使用accept方法将两个类连接在一起

# Official Diagram of the Visitor Pattern

# Client

聚合结构，包含多个节点

# Object Structure

# Visitor

visitElementA(ElementA)
visitElementB(ElementB)

为了某种目的，例如获得： price

为了某种目的：
例如，获得 Inventory

# ConcreteVisitor1

visitElementA(ElementA)
visitElementB(ElementB)

# ConcreteVisitor2

visitElementA(ElementA)
visitElementB(ElementB)

# Element

accept(Visitor)

# ElementA

accept(Visitor v)
operationA()

v.visitElementA(this)

# ElementB

accept(Visitor v)
operationB()

v.visitElementB(this)

# Visitor pattern class diagram

# Visitor Pattern

# 访问者模式构件的解释

- **Visitor class** declares a Visit operation for each class of Element in the object structure.
  - The operation's name and signature identifies the class that sends the Visit request to the visitor. For example, method visitHardDisk
  - Let the visitor determine the concrete class of the element being visited. Then the visitor can access the element directly through its particular interface.

# Visitor Pattern

# 访问者模式构件的解释

# ConcreteVisitor

> Implements each operation declared by Visitor.
> - Each operation implements a fragment of the algorithm defined for the corresponding class of object in the structure.
> Provides the context for the algorithm and stores its local state, which often accumulates results during the traversal of the structure.

# Visitor Pattern

# Element

- Defines an Accept operation that takes a visitor as an argument.

# ConcreteElement (ElementA, ElementB)

- Implements an “accept” operation that takes a visitor as an argument.
- May also implement some methods to help the visitor to realize some functionalities. For example, getData in Tax hierarchy

# Visitor Pattern

# ObjectStructure (Program) (can be omitted)

- Can enumerate its elements.
- May provide a high-level interface to allow the visitor to visit its elements.
- May either be a composite or a collection such as a list or a set.
- 该类可以使用一个聚合结构例如Java ArrayList将被访问对象集合在一起，然后再使用一个循环语句批量调用accept方法。

# 例2: E-bike parts store (电动自行车配件商店)

假如我们要为一个电动自行车专卖商店写一个销售程序。现在已经有一个层次类如下可供使用。

![](img/95717dc23f76db2057b9aa0c49790307_1074_0.png)

E-bike parts can be organized into a Hierarchy of classes
