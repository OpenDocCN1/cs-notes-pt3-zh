
## 生成器(Builder)

## 为何使用？

- 是为了将构建复杂对象的过程和它的部件解耦。注意：是解耦过程和部件。
- 因为一个复杂的对象,不但有很多大量组成部分,如汽车,有很多部件:车轮 方向盘 发动机还有各种小零件等等,部件很多,但远不止这些,如何将这些部件装配成一辆汽车,这个装配过程也很复杂(需要很好的组装技术),Builder模式就是为了将部件和组装过程分开。

## 生成器

![](img/b706331eacf49a62651c2c9b2de81ca5_1019_0.png)

## 需要一个接口,它定义如何创建复杂对象的各个部件

```
public interface Builder {
    //创建部件A    比如创建汽车车轮
    void buildPartA();
    //创建部件B 比如创建汽车方向盘
    void buildPartB();
    //创建部件C 比如创建汽车发动机
    void buildPartC();

    //返回最后组装成品结果 (返回最后装配好的汽车)
    //成品的组装过程不在这里进行,而是转移到下面的Director类中进行.
    //从而实现了解耦过程和部件
    Product getResult();
}
```

## Director的内容是如何将部件最后组装成成品

```
public class Director {
    private Builder builder;
    public Director( Builder builder ) {
        this.builder = builder;
    }
    // 将部件partA partB partC最后组成复杂对象
    // 这里是将车轮 方向盘和发动机组装成汽车的过程
    public void construct() {
        builder.buildPartA();
        builder.buildPartB();
        builder.buildPartC();
    }
}
```

## Product 和Part

复杂对象:产品Product:

```
public interface Product { }
```

复杂对象的部件:

```
public interface Part { }
```

## 如何调用Builder模式

```
public class Client
{
    private Director director;
    private Product product;
    private Builder builder = new ConcreteBuilder();

    public void requestBuild()
    {
        director = new Director( builder );
        director.construct();
        product = builder.getResult();
    }
}
```

## 单例模式(Singleton)

单例模式有以下的特点：

- 单例类只可有一个实例。
- 单例类必须自己创建自己这惟一的实例。
- 单例类必须给所有其他对象提供这一实例。

一个例子： Windows 回收站

Windows 9x 以后的视窗系统中都有一个回收站，下图就显示了 Windows 2000 的回收站。

![](img/b706331eacf49a62651c2c9b2de81ca5_1025_0.png)

在整个视窗系统中，回收站只能有一个实例，整个系统都使用这个惟一的实例，而且回收站自行提供自己的实例。因此，回收站是单例模式的应用。

## 单例模式(Singleton)

![](img/b706331eacf49a62651c2c9b2de81ca5_1026_0.png)

## 单例模式(Singleton)

```
public class EagerSingleton
{
    private static final EagerSingleton m_instance = new EagerSingleton();

    /**
     * 私有的默认构造子
     */
    private EagerSingleton() {}
    /**
     * 静态工厂方法
     */
    public static EagerSingleton getInstance()
    {
        return m_instance;
    }
}
```

## 单例模式(Singleton)

在这个类被加载时，静态变量 m_instance 会被初始化，此时类的私有构造子会被调用。这时候，单例类的惟一实例就被创建出来了。

Java 语言中单例类的一个最重要的特点是类的构造子是私有的，从而避免外界利用构造子直接创建出任意多的实例。值得指出的是，由于构造方法是私有的，因此，此类不能被继承。

## --结构型模式

这一类的模式关心类和对象之间怎么组织起来形成大的结构.

## 适配器（Adapter）模式

目的：

把一个类用用户希望的形式描述,即用用户希望的接口适配这个类。在这个模式中，这个类叫做被适配者（Adaptee），用户定义的接口叫适配接口，用户实现适配接口的类叫适配器（Adapter）。

## 例子：动物图形编辑器

![](img/b706331eacf49a62651c2c9b2de81ca5_1031_0.png)

重用

我们的程序

现成的程序

![](img/b706331eacf49a62651c2c9b2de81ca5_1031_1.png)

## 策略1—对象适配器

![](img/b706331eacf49a62651c2c9b2de81ca5_1032_0.png)

## 策略1—对象适配器

- //这是个适配器程序，适配Tiger使其具有Tookit的接口
- public class TigerAdaptor implements Tookit
- {
-     public Tiger theTiger;
-     public TigerAdaptor(Tiger t)
-     {
-         theTiger=t;
-     }
-     public void draw()
-     {
-         theTiger.paint();
-     }
- }
-

## 策略2—类适配器

![](img/b706331eacf49a62651c2c9b2de81ca5_1034_0.png)

## 策略2—采用继承

- public class TigerAdaptor1 extends Tiger implements Toolkit
- {
- public TigerAdaptor1()
- {
- }
- 
- public void draw()
- {
- super.paint();
- }
- }

## 设计模式之Proxy(代理)

- ■ 例子：Windows的快捷方式

![](img/b706331eacf49a62651c2c9b2de81ca5_1036_0.png)

## 设计模式之Proxy(代理)

设计模式中定义：

为其他对象提供一种代理以控制对这个对象的访问。

某个客户端不能直接操作到某个对象,但又必须和那个对象有所互动。

## 设计模式之Proxy(代理)

![](img/b706331eacf49a62651c2c9b2de81ca5_1038_0.png)

## 设计模式之Proxy(代理)

高三小姐的神貌和本人

悟空扮演并代替高三小姐

![](img/b706331eacf49a62651c2c9b2de81ca5_1039_0.png)

## 八戒分辨不出真假老婆

![](img/b706331eacf49a62651c2c9b2de81ca5_1040_0.png)

## 设计模式之Facade(门面)

门面模式要求一个子系统的外部与其内部的通信必须通过一个统一的门面（Facade）对象进行。门面模式提供一个高层次接口，使得子系统更易于使用。

![](img/b706331eacf49a62651c2c9b2de81ca5_1042_0.png)
