

## 结构型模式（Structural Pattern）

结构型模式涉及到如何组合类和对象以获得更大的结构。

（1）结构型类模式：采用继承机制来组合接口或实现。一个简单的例子是采用多重继承方法将两个以上的类组合成一个类，结果这个类包含了所有父类的性质。这一模式尤其有助于多个独立开发的类库协同工作。

（2）结构型对象模式：不是对接口和实现进行组合，而是描述了如何对一些对象进行组合，从而实现新功能的一些方法，采用聚集机制。因为可以在运行时刻改变对象组合关系，所以对象组合方式具有更大的灵活性，但这种机制涉及的类会比不使用类的多。

类模式和对象模式的区别在于：

（1）类模式描述了如何用继承来提供更有用的程序接口。
（2）对象模式则描述了如何使用对象组合或者在其他对象中包含对象的方式，将对象组合成更大的结构。

经典的结构型模式包含以下几种：

- ADAPTER（适配器）一类对象结构型模式
- BRIDGE（桥接）一对象结构型模式
- COMPOSITE（组合）一对象结构型模式
- DECORATOR（装饰）一对象结构型模式
- FACADE（外观）一对象结构型模式
- PROXY（代理）一对象结构型模式
- FLYWEIGHT（享元）一对象结构型模式

## 1. 适配器模式

### （1）概念或意图

适配器（Adapter）模式把一个类的接口变换成客户端所期待的另一种接口。从而使原本因为接口不匹配而无法在一起工作的两个类能够在一起工作。

若希望将无关的类组合在一个程序中协同工作时，就可以使用适配器模式——即编写一个有所需接口的类。然后令其与有着不同接口的类进行通信。实现这一要求的方法有两种：

- 一种是继承
- 一种是对象组合（聚集关系）。

第一种方法中，从一个非一致性的类中派生一个新类，并增加新的方法使派生类与所需接口匹配。

第二种方法中，在新类中包含最初的类，并创建方法来解释新类中的调用。

这两种方法分别称为类适配器和对象适配器。

### （2）适用性

以下情况使用 Adapter 模式：

- 想使用一个已经存在的类，而它的接口不符合你的需求。
- 想创建一个可以复用的类，该类可以与其他不相关的类或不可预见的类（即那些接口可能不一定兼容的类）协同工作。（译者注：想要建立一个可以重复使用的类，用于与一些彼此之间没有太大关联的一些类，包括一些可能在将来引进的类一起工作。）
- （仅适用于对象 Adapter）想使用一些已经存在的子类，但是不可能对每一个都进行子类化以匹配它们的接口。对象适配器可以适配它的父类接口。

### （3）结构

类适配器使用多重继承对一个接口与另一个接口进行匹配，如下图所示。

![](img/3b4669cf00b2833fe526284506f3f342_20_0.png)

对象匹配器依赖于对象组合，如下图所示。

![](img/3b4669cf00b2833fe526284506f3f342_20_1.png)

### （4）参与者

- Target（Shape）
  - 定义 Client 使用的与特定领域相关的接口。
- Client（DrawingEditor）
  - 与符合 Target 接口的对象协同。
- Adapter（TextView）
  - 定义一个已经存在的接口，这个接口需要适配。
- Adapter（TextShape）
  - 对 Adaptee 的接口与 Target 接口进行适配

### （5）协作

- Client 在 Adapter 实例上调用一些操作。接着适配器调用 Adaptee 的操作实现这个请求。

类适配器：

- 用一个具体的 Adapter 类对 Adaptee 和 Target 进行匹配。
- 使得 Adapter 可以重定义 Adaptee 的部分行为，因为 Adapter 是 Adaptee 的一个子类。
- 仅仅引入了一个对象，并不需要额外的指针以间接得到 Adaptee。

对象适配器：

- 允许一个 Adapter 与多个 Adaptee—即 Adaptee 本身以及它的所有子类（如果有子类的话）一同时工作。Adapter 也可以一次给所有的 Adaptee 添加功能。

例子：

问题描述：有一个绘图编辑器，这个编辑器允许用户绘制和排列基本图元（线、多边型和正文等）生成图片和图表。这个绘图编辑器的关键抽象是图形对象。图形对象有一个可编辑的形状，并可以绘制自身。图形对象的接口由一个称为Shape的抽象类定义。绘图编辑器为每一种图形对象定义了一个Shape的子类：LineShape类对应于直线，PolygonShape类对应于多边型，等等。

像LineShape和PolygonShape这样的基本几何图形的类比较容易实现，这是由于它们的绘图和编辑功能本来就很有限。但是对于可以显示和编辑正文的TextShape子类来说，实现相当困难，因为即使是基本的正文编辑也要涉及到复杂的屏幕刷新和缓冲区管理。同时，成品的用户界面工具箱可能已经提供了一个复杂的TextView类用于显示和编辑正文。

理想的情况是我们可以复用这个TextView类以实现TextShape类，但是工具箱的设计者当时并没有考虑Shape的存在，因此TextView和Shape对象不能互换。

怎么办？一个应用可能会有一些类具有不同的接口并且这些接口互不兼容。在这样的应用中象TextView这样已经存在并且不相关的类如何协同工作呢？我们可以改变TextView类使它兼容Shape类的接口，但前提是必须有这个工具箱的源代码。然而即使我们得到了这些源代码，修改TextView也是没有什么意义的：因为不应该仅仅为了实现一个应用，工具箱就不得不采用一些与特定领域相关的接口。

解决方法：我们可以不用上面的方法，而定义一个TextShape类，由它来适配TextView的接口和Shape的接口。我们可以用两种方法做这件事：
1）继承Shape类的接口和TextView的实现；
2）将一个TextView实例作为TextShape的组成部分，并且使用TextView的接口实现TextShape。这两种方法恰好对应于Adapter模式的类和对象版本。我们将TextShape称之为适配器Adapter。

上面的类图说明了**对象适配器实例**。它说明了在Shape类中声明的**BoundingBox**请求如何被转换成在TextView类中定义的**GetExtent**请求。由于TextShape将TextView的接口与Shape的接口进行了匹配，因此绘图编辑器就可以复用原先并不兼容的TextView类。

Adapter**时常还要负责提供那些匹配类的类所没有提供的功能，上面的类图中说明了适配器如何实现这些职责。由于绘图编辑器允许用户交互的将每一个Shape对象“拖动”到一个新的位置，而TextView设计中没有这种功能。我们可以实现TextShape类的CreateManipulator操作，从而增加这个缺少的功能，这个操作返回相应的Manipulator子类的一个实例。**

**Manipulator**是一个抽象类，它所描述的对象知道如何驱动Shape类响应相应的用户输入，例如将图形拖动到一个新的位置。对于不同形状的图形，Manipulator有不同的子类：例如子类TextManipulator对应于TextShape。TextShape通过返回一个TextManipulator实例，增加了TextView中缺少而Shape需要的功能。

```cpp
class Shape {
public:
    Shape();
    virtual void BoundingBox(
        Point& bottomLeft, Point& topRight
    ) const;
    virtual Manipulator* CreateManipulator() const;
};
```

```cpp
class TextView {
public:
    TextView();
    void GetOrigin(Coord& x, Coord& y) const;
    void GetExtent(Coord& width, Coord& height) const;
    virtual bool IsEmpty() const;
};
```

Shape假定有一个边框，这个边框由它相对的两角定义。而TextView则由原点、宽度和高度定义。Shape同时定义了CreateManipulator操作用于创建一个Manipulator对象。当用户操作一个图形时，Manipulator对象知道如何驱动这个图形。TextView没有等同的操作。TextShape类是这些不同接口间的适配器。

类适配器采用多重继承适配接口。类适配器的关键是用一个分支继承接口，而用另外一个分支继承接口的实现部分。通常C++中作出这一区分的方法是：用公共方式继承接口；用私有方式继承接口的实现（继承的是实现，即：要用到其父类的实现，所以父类一般不是抽象类，当然也不能通过virtual来声明TextView，就此而言）。因为公有继承代表的是接口的含义。下面按照这种常规方法定义TextShape适配器。

```cpp
class TextShape : public Shape, private TextView {
public:
    TextShape();
    virtual void BoundingBox(
        Point& bottomLeft, Point& topRight
    ) const;
    virtual bool IsEmpty() const;
    virtual Manipulator* CreateManipulator() const;
};
```

BoundingBox操作对TextView的接口进行转换使之匹配 Shape的接口。

```cpp
void TextShape::BoundingBox (
    Point& bottomLeft, Point& topRight
) const {
    Coord bottom, left, width, height;
    GetOrigin(bottom, left);
    GetExtent(width, height);
    bottomLeft = Point(bottom, left);
    topRight = Point(bottom + height, left + width);
}
```

对象适配器采用对象组合的方法将具有不同接口的类组合在一起。在该方法中，适配器TextShape维护一个指向TextView的指针。

```cpp
class TextShape : public Shape {
public:
    TextShape(TextView*);
    virtual void BoundingBox(
        Point& bottomLeft, Point& topRight
    ) const;
    virtual bool IsEmpty() const;
    virtual Manipulator* CreateManipulator() const;
private:
    TextView* _text;
};
```

TextShape必须在构造器中对指向TextView实例的指针进行初始化，当它自身的操作被调用时，它还必须对它的TextView对象调用相应的操作。在本例中，假设客户创建了TextView对象并且将其传递给TextShape的构造器：

