# 第十二章 基于对象的分布式系统

# 12.2 CORBA

# ◆CORBA的POA

如何使用一个雇佣来构建一个CORBA对象的映像的呢？

+   - 每个POA提供如下操作：

```
Objectid activate_object(in Servant p_servant);
```

这个操作已经在CORBA IDL中说明。这个操作的输入参数是一个指向某个雇佣的指针，返回值是一个CORBA对象的标识符。

+   - C++中，雇佣被映射成为一个指针，该指针指向一个事先定义好的ServantBase类。这个类中包含了一组方法定义，这些方法定义要求每个C++雇佣必须实现。