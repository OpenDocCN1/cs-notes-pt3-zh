# 桥接模式

桥接模式包含如下角色

+   - Abstraction：抽象类，用于定义抽象类的接口，一般是抽象类而不是接口，其中定义了一个Implementor（实现类接口）类型对象并可以维护该对象，它与Implementor之间具有关联关系，它既可以包含抽象业务方法，也可以包含具体业务方法。

+   - RefinedAbstraction：扩充抽象类，扩充由Abstraction定义的接口，通常情况下它不再是抽象类而是具体类，它实现了在Abstraction中声明的抽象业务方法，也可以调用在Implementor中定义的业务方法。