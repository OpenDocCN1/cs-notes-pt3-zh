# 多态

+   多态
+   多种实现方式提供服务

+   动态绑定

+   向上转型
+   把引用变量转换为父类类型

+   向下转型
+   把引用变量转换为子类类型

```
Pet pet = new Dog();
Dog dog = (Dog)pet; //向下转型
Animal animal = pet; //向上转型
```