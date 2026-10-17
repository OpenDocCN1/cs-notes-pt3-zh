抽象工厂类FruitGardener 是工厂方法模式的核心，但是它并不掌握水果类或蔬菜类的生成大权。相反地，这项权力被交给子类，即AppleGardener StrawberryGardener 以及GrapeGardener。

# # 工厂角色的等级结构

各个工厂角色组成一个工厂的等级结构，如下图所示。

![](bbox=[0.194, 0.291, 0.688, 0.473])

在上图所示的等级结构中，FruitGardener 是所有具体工厂角色的超类。在本系统中，这个抽象角色是由Java 接口FruitGardener 接口实现的，它声明了一个工厂方法，要求所有的具体工厂角色都要实现这个工厂方法。
这个角色的源代码如下所示。
第13 章工厂方法（Factory Method）模式 • 175 •
代码清单8：抽象工厂角色FruitGardener 的源代码
package com.javapatterns.factorymethod.farm;
public interface FruitGardener
{
/**
* 工厂方法
*/
public Fruit factory();
}
AppleGardener 类是具体工厂类，它实现了FruitGardener 接口，提供了工厂方法的实现。
它的源代码如下所示。
代码清单9：具体工厂类AppleGardener 的源代码
package com.javapatterns.factorymethod.farm;
public class AppleGardener
implements FruitGardener
{
/**
* 工厂方法
*/
public Fruit factory()
{