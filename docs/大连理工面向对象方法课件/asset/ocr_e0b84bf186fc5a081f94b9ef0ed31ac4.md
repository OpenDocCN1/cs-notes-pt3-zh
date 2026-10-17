```
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

具体产品类 Strawberry 的源代码如代码清单 14 所示。
package com.javapatterns.factorymethod.farm;

# public class Strawberry implements Fruit//具体产品

```
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

Grape 类也是一个具体产品角色，如代码清单 15 所示。
package com.javapatterns.factorymethod.farm;

# public class Grape implements Fruit//具体产品

```
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
}
```