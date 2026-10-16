
# Bridge Pattern

# Implementor

+   - Defines the interface for implementation classes.
+   - This interface doesn't have to correspond exactly to Abstraction's interface; in fact the two interfaces can be **quite different**.

# Bridge Pattern

# Typically

+   - The Implementor interface provides only primitive operations（实现接口仅提供原始操作）
+   - The Abstraction defines higher-level operations based on these primitives（抽象接口定义基于原始操作的高层操作）

# Bridge Pattern

The ConcreteImplementors:

+   - **ImplementorA and**
+   - **ImplementorB**

implement the Implementor interface and defines its concrete implementation.

# Advantages of Bridge Pattern

# 桥模式的优点

+   1. 将接口与实现解耦。 Decoupling interface and implementation.

An implementation is not bound permanently to an interface

+   - The implementation of an abstraction can be configured at run-time (实现部分动态配置)

+   - Decoupling Abstraction and Implementor also eliminates compile-time dependencies on the implementation (取消编译时对实现部分的依赖)

+   - Changing an implementation class doesn't require recompiling the Abstraction class and its clients (改变实现类不需要重新编译抽象类与客户端)

# Advantages of Bridge Pattern

2. 改善了可扩展性。 Extensibility Improvement
You can extend the Abstraction and Implementor hierarchies independently.

3. 对用户隐藏实现细节。 Hiding implementation details from clients.
You can shield clients from implementation details, like the sharing of implementor objects and the accompanying reference count mechanism (if any).

# Bridge Pattern

# 何时使用桥模式？

# When to use the bridge pattern?

**Applicability**: Use the Bridge pattern when you want to avoid a permanent binding between an abstraction and its implementation.

+   - e. g. when the implementation must be selected or switched at run-time.

# Bridge Pattern

桥的一种功能

![](img/95717dc23f76db2057b9aa0c49790307_619_0.png)

一座桥与6条路，一共有 2 X 3 = 6 种走法

# Bridge Pattern

桥接模式的典型交互

```
CoffeeKind cKind = new MilkCoffee();
CoffeeSize cSize = SuperSize(cKind);
cSize.getPrice();
```

cSize.getPrice();

return 1.5*1.2元

return 1.2元

cKind.price()

桥接模式的典型交互-咖啡机程序的例子

# Design Examples Using the Bridge Pattern

# 应用桥模式设计的例子

【例2】考虑一个自动茶水销售机的例子，该机器销售的茶水价格与两个维度：杯子大小与茶叶品种有关。

+   - 杯子的体积上暂时分为中杯，大杯；
+   - 在茶叶品种上，分为红茶，和绿茶。

# 应用桥模式设计的例子

按照桥模式设计，类图如下。

![](img/95717dc23f76db2057b9aa0c49790307_623_0.png)

# Bridge Pattern

桥接模式的典型交互

```
TeaKind tKind = new RedTea();
TeaSize tSize = SuperCup(tKind);
tSize.getPrice();
```

Client

tSize.getPrice();

TeaSize

MedCup
+getPrice()

SuperCup
+getPrice()

return 1.5*1.2

TeaKind

tKind.price()

RedTea
+price()

GreenTea
+price()

return 1.2

茶水程序的典型交互情况

Choose Cup Size Super Cup

Choose Tea Kind Red Tea

Tea Price: 4.5 dollars

Find Price

Exit

# 应用桥模式设计的例子

```
class ButtonListener implements ActionListener {
    public void actionPerformed(ActionEvent e) {
        if (e.getActionCommand().equals( FINDPRICE )) {
            String size = getTeaSize(); //获得用户输入： 杯子大小
            String kind = getTeaKind(); //获得用户输入： 茶种类
            //Create a TeaKind object
            if( kind.compareTo(GREENTEA)==0 )
                tKind = new GreenTea();
            if( kind.compareTo(REDTEA)==0 )
                tKind = new RedTea();
            if(size.compareTo(SUPERCUP)==0)
                tSize = new SuperCup(tKind);
            if(size.compareTo(MEDIUMCUP)==0)
                tSize = new MediumCup(tKind);
            float price = tSize.getPrice();
        }
    }
}
```

创建TeaKind对象

创建TeaSize对象

# 应用桥模式设计的例子

# 抽象接口类

```
public interface TeaSize {
    public abstract float getPrice();
}
```

# 抽象部分子类

```
public class MediumCup implements TeaSize{
    private TeaKind tk;
    public MediumCup (TeaKind tKind){
        tk = tKind;
    }
    public float getPrice(){
        float teaPrice = tk.price();
        return teaPrice;
    }
}
```

# 应用桥模式设计的例子

# 抽象部分子类

```
public class SuperCup implements TeaSize{
    private TeaKind tk;
    public SuperCup (TeaKind tKind){
        tk = tKind;
    }
    public float getPrice(){
        float teaPrice = 1.5f * tk.price();
        return teaPrice;
    }
}
```
