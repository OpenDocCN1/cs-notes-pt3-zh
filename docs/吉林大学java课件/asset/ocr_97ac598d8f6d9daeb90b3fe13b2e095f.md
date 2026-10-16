# 依赖倒转原则

# 依赖倒转原则分析

依赖注入： 一个类依赖另一个类来实现功能，但不在该类内部实例化被依赖类，而是通过一些方法注入被用来的对象。

+   - 构造注入(Constructor Injection)： 通过构造函数注入实例变量。

+   - 设值注入(Setter Injection)： 通过Setter方法注入实例变量。

+   - 接口注入(Interface Injection)： 通过接口方法注入实例变量。