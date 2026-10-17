```
return new Apple();
}
}
```

StrawberryGardener 类是一个具体工厂类，与AppleGardener 一样，它也实现了FruitGardener 接口。此类的源代码如下所示。

# 代码清单10: 具体工厂类StrawberryGardener 的源代码

```
package com.javapatterns.factorymethod.farm;
public class StrawberryGardener
implements FruitGardener
{
/**
* 工厂方法
*/
public Fruit factory()
{
return new Apple();
}
}
```

同样，具体类GrapeGardenter 的源代码如下所示。

# 代码清单11: 具体工厂类GrapeGardener 的源代码

```
package com.javapatterns.factorymethod.farm,
public class GrapeGardener
implements FruitGardener
{
/**
* 工厂方法
*/
public Fruit factory()
{
return new Apple();
}
}
```

# 产品角色的等级结构

所有的产品角色都属于一个产品的等级结构，在这个等级结构最上面的是抽象产品角
色Product。在本系统中，这个角色是由一个Java 接口Fruit 实现的。由各个工厂角色组成
的工厂等级结构如下图所示。