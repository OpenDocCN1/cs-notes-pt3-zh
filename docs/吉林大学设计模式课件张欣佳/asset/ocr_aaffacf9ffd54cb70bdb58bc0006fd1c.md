# Visitor

+ visitConcreteElementA(
ConcreteElementA elementA)
+ visitConcreteElementB(
ConcreteElementB elementB)

# Client

# ConcreteVisitorA

+ visitConcreteElementA(
ConcreteElementA elementA)
+ visitConcreteElementB(
ConcreteElementB elementB)

# ConcreteVisitorB

+ visitConcreteElementA(
ConcreteElementA elementA)
+ visitConcreteElementB(
ConcreteElementB elementB)

# ObjectStructure

# Element

+ accept (Visitor visitor)

# ConcreteElementA

+ accept (Visitor visitor)
+ operationA ()

```
visitor.visitConcreteElementA(this);
```

# ConcreteElementB

+ accept (Visitor visitor)
+ operationB ()

```
visitor.visitConcreteElementB(this);
```