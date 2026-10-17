![](bbox=[0.184, 0.104, 0.803, 0.402])

所有具体产品都必须实现抽象产品 Fruit 所声明的接口，如代码清单 12 所示。

# 代码清单 12：抽象产品角色 Fruit 的源代码

```
package com.javapatterns.factorymethod.farm;
public interface Fruit//抽象产品
{
void grow();
void harvest();
void plant();
}
```

Apple 类是一个具体产品类，实现了 Fruit 接口，如代码清单 13 所示。

# 代码清单 13：水果类 Apple 的源代码

```
package com.javapatterns.factorymethod.farm;
public class Apple implements Fruit//具体产品
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
}
```