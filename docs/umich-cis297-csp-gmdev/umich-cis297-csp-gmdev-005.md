# 005：继承与多态 🎮

在本节课中，我们将要学习面向对象编程中两个核心概念：**继承**与**多态**。我们将通过构建一个多边形（Polygon）类及其子类（如三角形、梯形）的例子，来理解抽象类、方法重写、类型转换以及访问修饰符（如 `protected`）的用法。课程内容旨在让初学者能够轻松理解这些概念。

## 概述

上一节我们介绍了类的基本概念和构造函数。本节中，我们来看看如何通过继承来创建具有层次关系的类，并利用多态性让程序在运行时表现出不同的行为。

---

## 抽象类与抽象方法

![](img/8f63bde97dd5b09be17f3d6ac3f25454_1.png)

我们有一个 `Polygon` 类，它可以创建多边形，但一个通用的多边形无法计算面积。因此，我们将 `Polygon` 类标记为**抽象类**，并将计算面积的 `Area` 方法标记为**抽象方法**。

![](img/8f63bde97dd5b09be17f3d6ac3f25454_3.png)

```csharp
public abstract class Polygon
{
    protected double[] sideLengths;
    public string Name { get; set; }

    public Polygon(int numberOfSides, string name)
    {
        sideLengths = new double[numberOfSides];
        Name = name;
    }

    // 抽象方法，没有方法体，必须在派生类中实现
    public abstract double Area();
}
```

**关键点**：
*   抽象类使用 `abstract` 关键字修饰。
*   抽象类**不能**被实例化（即不能使用 `new Polygon()`）。
*   抽象方法只有声明，没有实现（没有方法体 `{}`）。
*   任何继承自抽象类的非抽象子类**必须**实现（重写）其所有的抽象方法。

---

## 实现子类：三角形与梯形

![](img/8f63bde97dd5b09be17f3d6ac3f25454_5.png)

现在，我们创建两个继承自 `Polygon` 的具体类：`Triangle` 和 `Trapezoid`。它们必须实现 `Area` 方法。

![](img/8f63bde97dd5b09be17f3d6ac3f25454_7.png)

### 三角形 (Triangle)

![](img/8f63bde97dd5b09be17f3d6ac3f25454_9.png)

![](img/8f63bde97dd5b09be17f3d6ac3f25454_11.png)

三角形的面积公式为：**底 * 高 / 2**。为简化，我们假设这是一个等边三角形，面积公式为：

![](img/8f63bde97dd5b09be17f3d6ac3f25454_13.png)

**面积 = (√3 / 4) * 边长²**

```csharp
public class Triangle : Polygon
{
    public Triangle(string name) : base(3, name) { }

    public override double Area()
    {
        double side = sideLengths[0]; // 假设是等边三角形
        return (Math.Sqrt(3) / 4.0) * side * side;
    }
}
```

![](img/8f63bde97dd5b09be17f3d6ac3f25454_15.png)

![](img/8f63bde97dd5b09be17f3d6ac3f25454_17.png)

![](img/8f63bde97dd5b09be17f3d6ac3f25454_19.png)

### 梯形 (Trapezoid)

![](img/8f63bde97dd5b09be17f3d6ac3f25454_21.png)

![](img/8f63bde97dd5b09be17f3d6ac3f25454_23.png)

梯形的面积公式为：**(上底 + 下底) * 高 / 2**。我们需要根据给定的边长计算高度。以下是计算梯形面积的代码实现：

```csharp
public class Trapezoid : Polygon
{
    // 定义各边的索引，提高代码可读性
    public static readonly int BottomSideIndex = 0;
    public static readonly int TopSideIndex = 2;
    public static readonly int LeftSideIndex = 1;
    public static readonly int RightSideIndex = 3;

    public Trapezoid(string name) : base(4, name) { }

    // 重写设置边长的方法，确保左右腰等长
    public override void SetSideLength(int index, double length)
    {
        if (index == LeftSideIndex || index == RightSideIndex)
        {
            // 设置左腰或右腰时，同时设置另一腰
            sideLengths[LeftSideIndex] = length;
            sideLengths[RightSideIndex] = length;
        }
        else
        {
            base.SetSideLength(index, length);
        }
    }

    public override double Area()
    {
        double bottom = sideLengths[BottomSideIndex];
        double top = sideLengths[TopSideIndex];
        double leg = sideLengths[LeftSideIndex]; // 腰长

        // 计算高度公式：h = √(c² - ((a - b)/2)²)
        // 其中 c 是腰长，a 是下底，b 是上底
        double baseDifference = (bottom - top) / 2.0;
        double height = Math.Sqrt((leg * leg) - (baseDifference * baseDifference));

        // 梯形面积公式
        return (bottom + top) * height / 2.0;
    }
}
```

**代码说明**：
*   `: base(4, name)` 调用父类 `Polygon` 的构造函数。
*   `override` 关键字用于重写父类中的虚方法或抽象方法。
*   我们通过定义 `static readonly` 字段（如 `BottomSideIndex`）来使代码意图更清晰，这是一种良好的编程实践。

![](img/8f63bde97dd5b09be17f3d6ac3f25454_25.png)

---

![](img/8f63bde97dd5b09be17f3d6ac3f25454_27.png)

## 运行时类型检查与多态

多态允许我们使用父类类型（如 `Polygon`）的引用来指向子类对象，并在运行时确定其实际类型，从而调用正确的方法。

以下是检查对象类型并安全进行类型转换的两种方法：

**方法一：使用 `is` 和 `as` 关键字**
这是更安全、更简洁的现代写法。

![](img/8f63bde97dd5b09be17f3d6ac3f25454_29.png)

```csharp
foreach (Polygon poly in polygonList)
{
    // 使用 `as` 尝试转换，失败则返回 null
    Trapezoid trap = poly as Trapezoid;
    if (trap != null)
    {
        // 现在可以安全地调用 Trapezoid 特有的方法
        Console.WriteLine("这是一个梯形");
    }
}
```

![](img/8f63bde97dd5b09be17f3d6ac3f25454_31.png)

**方法二：使用 `GetType()` 和 `typeof()`**
这种方法更直接，但不如第一种灵活。

```csharp
foreach (Polygon poly in polygonList)
{
    if (poly.GetType() == typeof(Trapezoid))
    {
        // 确定类型后，可以进行强制转换
        Trapezoid trap = (Trapezoid)poly;
        Console.WriteLine("这是一个梯形");
    }
}
```

**核心概念**：
*   **多态**：同一个操作作用于不同的对象，可以有不同的解释和执行结果。在这里，`poly.Area()` 会根据 `poly` 实际是三角形还是梯形调用不同的 `Area` 实现。
*   **类型转换**：将对象从一种类型转换为另一种类型。`as` 关键字进行安全转换，失败返回 `null`；直接强制转换 `(Trapezoid)poly` 失败则会抛出异常。

![](img/8f63bde97dd5b09be17f3d6ac3f25454_33.png)

![](img/8f63bde97dd5b09be17f3d6ac3f25454_35.png)

---

## 访问修饰符：protected

在父类中，如果将字段标记为 `private`，子类将无法直接访问。若希望子类能直接访问父类的某些成员，同时又不向外部公开，可以使用 `protected` 访问修饰符。

![](img/8f63bde97dd5b09be17f3d6ac3f25454_37.png)

```csharp
public abstract class Polygon
{
    // 子类可以直接访问 sideLengths，但其他外部类不能
    protected double[] sideLengths;
    // ... 其他成员
}
```

![](img/8f63bde97dd5b09be17f3d6ac3f25454_39.png)

![](img/8f63bde97dd5b09be17f3d6ac3f25454_41.png)

![](img/8f63bde97dd5b09be17f3d6ac3f25454_43.png)

在 `Trapezoid` 类中，我们可以直接操作 `sideLengths` 数组：
```csharp
sideLengths[BottomSideIndex] = 10.0; // 合法，因为是 protected
```

![](img/8f63bde97dd5b09be17f3d6ac3f25454_45.png)

访问修饰符总结：
*   `public`：完全公开。
*   `private`：仅本类内部可访问（默认）。
*   `protected`：本类及其派生类可访问。
*   `internal`：同一程序集内可访问。

![](img/8f63bde97dd5b09be17f3d6ac3f25454_47.png)

---

## 其他重要概念

![](img/8f63bde97dd5b09be17f3d6ac3f25454_49.png)

### sealed 关键字
`sealed` 修饰符可以应用于类或方法。
*   **密封类**：阻止其他类继承自此类。例如：`public sealed class MyFinalClass { ... }`
*   **密封方法**：在重写父类方法后，阻止派生类进一步重写此方法。

### 关于 `new` 关键字（警告）
在继承中，有时编译器会建议使用 `new` 关键字来“隐藏”父类方法，而不是 `override`（重写）。

![](img/8f63bde97dd5b09be17f3d6ac3f25454_51.png)

![](img/8f63bde97dd5b09be17f3d6ac3f25454_53.png)

```csharp
public class ChildClass : ParentClass
{
    public new void SomeMethod() { ... } // 隐藏父类方法，不推荐！
}
```

![](img/8f63bde97dd5b09be17f3d6ac3f25454_55.png)

**强烈建议**：除非你完全理解其含义并确有特殊需要，否则**永远不要**使用 `new` 关键字来隐藏父类成员。这会导致令人困惑的行为，破坏了多态性。应始终使用 `override` 来重写虚方法或抽象方法。

![](img/8f63bde97dd5b09be17f3d6ac3f25454_57.png)

---

![](img/8f63bde97dd5b09be17f3d6ac3f25454_59.png)

## 总结

![](img/8f63bde97dd5b09be17f3d6ac3f25454_61.png)

本节课中我们一起学习了面向对象编程的支柱之一：继承与多态。

我们掌握了以下核心技能：
1.  如何创建**抽象类**和**抽象方法**来定义不完整的模板。
2.  如何通过继承创建子类，并使用 `override` 关键字实现或重写父类方法。
3.  如何利用**多态性**，用父类类型引用子类对象，并在运行时通过 `is`/`as` 或 `GetType()` 检查具体类型。
4.  了解了 `protected` 访问修饰符的作用，它允许子类访问父类的特定成员。
5.  认识到应避免使用 `new` 关键字来隐藏继承的成员，而应优先使用 `override`。

![](img/8f63bde97dd5b09be17f3d6ac3f25454_63.png)

![](img/8f63bde97dd5b09be17f3d6ac3f25454_65.png)

这些概念是构建复杂、可维护的C#应用程序的基石。在接下来的项目中，你将有机会实践这些知识，构建更丰富的功能。