关联关系(Association) 是类与类之间最常用的一种关系，它是一种结构化关系，用于表示一类对象与另一类对象之间有联系。

在UML类图中，用实线连接有​​关联的对象所对应的类，在使用Java、C#和C++等编程语言实现关联关系时，通常将一个类的对象作为另一个类的属性。

+   1）双向关联：默认情况下，关联是双向的。

![](bbox=[0.147, 0.305, 0.849, 0.491])

```
public class Customer
{
    private Product[] products;
    ......
}
public class Product
{
    private Customer customer;
    ......
}
```