
## 再看“简单工厂”

### 一. 例子：农场专门向市场销售各类水果<sup>9138</sup>

### 结构与代码

![](img/3b4669cf00b2833fe526284506f3f342_30_0.png)

水果接口规定出所有的水果必须实现的接口，包括任何水果类必须具备的方法：种植plant()，生长grow()以及收获harvest()。

### 接口 Fruit 的源代码：

```
package com.javapatterns.factorymethod.farm;

public interface Fruit
{
    void grow();
    void harvest();
    void plant();
}
```

### Apple 类的源代码：

```
public class Apple implements Fruit
{
    private int treeAge;
    public void grow()
    {
        System.out.println("Apple is growing...");
    }
    public void harvest()
    {
        System.out.println("Apple has been harvested.");
    }
    public void plant()
    {
        System.out.println("Apple has been planted.");
    }
    public int getTreeAge()
    {
        return treeAge;
    }
    public void setTreeAge(int treeAge)
    {
        this.treeAge = treeAge;
    }
}
```

### Grape 类的源代码：

```
package com.javapatterns.factorymethod.farm;

public class Grape implements Fruit
{
    public void grow()
    {
        System.out.println("Grape is growing...");
    }
    public void harvest()
    {
        System.out.println("Grape has been harvested.");
    }
    public void plant()
    {
        System.out.println("Grape has been planted.");
    }
    public boolean getSeedless()
    {
        return seedless;
    }
    public void setSeedless(boolean seedless)
    {
        this.seedless = seedless;
    }
    private boolean seedless;
}
```

### Strawberry 类的源代码：

```
public class Strawberry implements Fruit
{
    public void grow()
    {
        System.out.println("Strawberry is growing...");
    }
    public void harvest()
    {
        System.out.println("Strawberry has been harvested.");
    }
    public void plant()
    {
        System.out.println("Strawberry has been planted.");
    }
}
```

### FruitGardener 园丁类的源代码

该类会根据客户端的要求创建出不同的水果类对象（实例），而如果水果类不合法，会抛出 BadFruitException 异常。

```
public class FruitGardener
{
    public static Fruit factory(String which) throws BadFruitException
    {
        if(which.equalsIgnoreCase("apple"))
        {
            return new Apple();
        }
        else if(which.equalsIgnoreCase("strawberry"))
        {
            return new Strawberry();
        }
        else if(which.equalsIgnoreCase("grape"))
        {
            return new Grape();
        }
        else
        {
            throw new BadFruitException("Bad fruit request");
        }
    }
}
```

园丁类提供了一个工厂方法。在客户端的调用下，这个方法创建客户端所需要的水果对象。如果客户端的请求是系统所不支持的，工厂方法就会抛出一个 BadFruitException 异常。

### 异常类 BadFruitException 源代码：

```
public class BadFruitException extends Exception
{
    public BadFruitException(String msg)
    {
        super(msg);
    }
}
```

在使用时，客户端只需调用 FruitGardener 的静态方法 factory()即可。

客户端代码如下：

```
try
{
    FruitGardener.factory("grape");
    FruitGardener.factory("apple");
    FruitGardener.factory("strawberry");
    ...
}
catch(BadFruitException e)
{
    ...
}
```

### 二. 总结：简单工厂模式的一般结构

简单工厂模式就是由一个工厂类根据传入的参量决定创建出哪一种产品类的实例。下面以一个示意性的实现为例说明简单工厂模式的结构，见下图：

![](img/3b4669cf00b2833fe526284506f3f342_33_0.png)

从图中可以看出，简单工厂模式涉及到工厂角色、抽象产品角色以及具体产品角色等三个角色：

- 1. 工厂类角色（Creator）：担任该角色的是工厂方法模式的核心，含有与应用紧密相关的商业逻辑。工厂类在客户端的直接调用下创建产品对象，它往往由一个具体 Java/C++类实现。
- 2. 抽象产品角色（product）：担任该角色的类是由工厂方法模式所创建的对象的父类，或他们共同拥有的接口。抽象产品角色可以用一个 Java 接口或 Java/C++抽象类实现。
- 3. 具体产品角色（Concrete Product）：工厂方法模式所创建的任何对象都是该角色的实例，具体产品角色由一个具体 Java/C++类实现。

### 源代码：

```
public class Creator//工厂类角色
{
    public static Product factory()
    {
        return new ConcreteProduct();
    }
}
```

抽象产品角色的主要目的是给所有的具体产品类提供一个共同的类型，在简单的情况下，可以简化为一个标识接口（没有声明任何方法的空接口）。

```
public interface Product//抽象产品角色
{
}
```

### 具体产品角色 ConcreteProduct 源代码：

```
public class ConcreteProduct implements Product//具体产品角色
{
    public ConcreteProduct(){
    }
}
```

虽然这个简单的示意性实现只给出了一个具体产品类，但是在实际应用中一般都会遇到多个具体产品类的情况。

### 回头看“姓，名”和“名 姓”的例子

### 简单工厂模式的优缺点

在简单工厂模式中，一个工厂类处于对产品类实例化的中心位置上，它知道每一个产品，它决定哪一个产品类应当被实例化。这个模式的优点是允许客户端相对独立于产品创建的过程，并且在系统引入新产品客户端的修改简单，也就是说，它在某种程度上支持“开-闭”原则。

缺点：是对“开-闭”原则的支持不够，因为如果有新的产品加入到系统中去，就需要修改工厂类，将必要的逻辑加入到工厂类中。
