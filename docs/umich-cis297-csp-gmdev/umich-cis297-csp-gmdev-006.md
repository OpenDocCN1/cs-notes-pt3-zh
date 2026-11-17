# 006：空值处理与继承



![](img/6fd630df18ef8be921ebbea0afd081fa_4.png)

在本节课中，我们将学习C#中两个重要的概念：如何处理可能为空的引用类型（空值处理），以及如何通过继承来创建类之间的层次关系。我们将通过构建一个简单的图形用户界面应用来演示这些概念。

![](img/6fd630df18ef8be921ebbea0afd081fa_6.png)

---

## 静态成员

上一节我们介绍了类的实例属性和方法。本节中我们来看看属于类本身，而不是任何特定实例的成员：静态成员。



![](img/6fd630df18ef8be921ebbea0afd081fa_12.png)

静态成员属于类级别，在所有实例间共享。它们常用于存储类相关的全局数据或提供无需实例即可调用的工具方法。

![](img/6fd630df18ef8be921ebbea0afd081fa_14.png)

以下是静态字段和静态方法的示例：

![](img/6fd630df18ef8be921ebbea0afd081fa_16.png)

```csharp
public class Student
{
    // 静态字段，用于生成唯一的学生ID
    private static int _nextId = 1000000;

    // 实例属性
    public int Id { get; private set; }
    public string Name { get; set; }

    // 构造函数
    public Student(string name)
    {
        Name = name;
        // 使用静态字段为实例属性赋值，然后递增
        Id = _nextId++;
    }

    // 静态方法：计算学费（不依赖于任何特定学生实例）
    public static decimal CalculateTuition(int credits)
    {
        return credits * 675m; // 假设每学分675美元
    }
}
```

在上面的代码中，`_nextId` 是一个静态字段，每次创建新的 `Student` 实例时，它都会递增，确保每个学生获得唯一的ID。`CalculateTuition` 是一个静态方法，因为它执行的计算不依赖于任何特定学生的数据。

---

## 空值处理

在C#中，引用类型（如类）的变量可以包含 `null`，表示它不引用任何对象。尝试在 `null` 引用上调用方法或访问属性会导致程序崩溃（抛出 `NullReferenceException`）。因此，正确处理可能的空值是编写健壮代码的关键。

### 空条件运算符 `?.`

![](img/6fd630df18ef8be921ebbea0afd081fa_18.png)

![](img/6fd630df18ef8be921ebbea0afd081fa_20.png)

空条件运算符允许你在访问成员之前安全地检查对象是否为 `null`。如果对象为 `null`，则表达式的结果为 `null`，不会执行后续操作。

![](img/6fd630df18ef8be921ebbea0afd081fa_22.png)

![](img/6fd630df18ef8be921ebbea0afd081fa_24.png)


![](img/6fd630df18ef8be921ebbea0afd081fa_26.png)

```csharp
// 假设 `section` 是一个可能为 null 的 Section 对象
List<Student> studentList = section?.GetStudents();
// 如果 section 为 null，则 studentList 也为 null，不会抛出异常。
```

![](img/6fd630df18ef8be921ebbea0afd081fa_28.png)

![](img/6fd630df18ef8be921ebbea0afd081fa_30.png)

### 空合并运算符 `??`

![](img/6fd630df18ef8be921ebbea0afd081fa_32.png)

空合并运算符提供了一种简洁的方式，在表达式结果为 `null` 时提供一个默认值。

```csharp
// 如果 GetStudents() 返回 null，则使用一个新的空列表
List<Student> students = section.GetStudents() ?? new List<Student>();
```

### 可空引用类型 `?`

从C# 8.0开始，你可以使用 `?` 后缀显式声明一个引用类型可以为 `null`。这有助于编译器提供警告，提醒你进行空值检查。


![](img/6fd630df18ef8be921ebbea0afd081fa_34.png)

![](img/6fd630df18ef8be921ebbea0afd081fa_36.png)

```csharp
public class Student
{
    public string Name { get; set; }
    public string? PhoneNumber { get; set; } // PhoneNumber 可能为 null
    public string? Email { get; set; }       // Email 可能为 null
}
// 使用时进行检查
if (student.Email != null)
{
    // 在此作用域内，编译器知道 Email 不为 null
    Console.WriteLine(student.Email.Contains("@"));
}
```

通过结合使用这些运算符和语法，你可以编写出既安全又简洁的代码来处理潜在的 `null` 值。

---

![](img/6fd630df18ef8be921ebbea0afd081fa_38.png)

![](img/6fd630df18ef8be921ebbea0afd081fa_40.png)

## 继承与多态

继承是面向对象编程的核心概念之一，它允许我们基于现有类（基类或父类）创建新类（派生类或子类）。派生类继承基类的成员，并可以添加新成员或重写基类的行为。

![](img/6fd630df18ef8be921ebbea0afd081fa_42.png)

### 创建基类

![](img/6fd630df18ef8be921ebbea0afd081fa_44.png)

让我们从一个简单的 `Polygon`（多边形）基类开始。

![](img/6fd630df18ef8be921ebbea0afd081fa_46.png)

![](img/6fd630df18ef8be921ebbea0afd081fa_48.png)

```csharp
public class Polygon
{
    private List<int> _sideLengths;
    public string Name { get; set; }

    // 构造函数
    public Polygon(int numberOfSides, string name)
    {
        Name = name;
        _sideLengths = new List<int>(numberOfSides);
        for (int i = 0; i < numberOfSides; i++)
        {
            _sideLengths.Add(0); // 初始化边长为0
        }
    }

    // 设置边长
    public virtual void SetSideLength(int sideIndex, int length)
    {
        _sideLengths[sideIndex] = length;
    }

    // 获取边长
    public int GetSideLength(int sideIndex)
    {
        return _sideLengths[sideIndex];
    }

    // 计算周长（属性）
    public int Perimeter => _sideLengths.Sum();

    // 计算面积（虚方法，将在派生类中被重写）
    public virtual double Area()
    {
        throw new NotImplementedException("面积计算依赖于具体多边形类型。");
    }

    // 重写 ToString 方法
    public override string ToString()
    {
        return $"{Name}: 面积 = {Area():F2}, 周长 = {Perimeter}";
    }
}
```

![](img/6fd630df18ef8be921ebbea0afd081fa_50.png)

注意 `SetSideLength` 和 `Area` 方法被标记为 `virtual`。这意味着它们可以在派生类中被**重写** (`override`)。

![](img/6fd630df18ef8be921ebbea0afd081fa_52.png)

![](img/6fd630df18ef8be921ebbea0afd081fa_54.png)

### 创建派生类：Rectangle

现在，我们创建一个 `Rectangle`（矩形）类，它继承自 `Polygon`。

![](img/6fd630df18ef8be921ebbea0afd081fa_56.png)

```csharp
public class Rectangle : Polygon // 使用冒号表示继承
{
    // 构造函数：矩形总是有4条边
    public Rectangle(string name) : base(4, name)
    {
    }

    // 更方便的构造函数，允许设置长和宽
    public Rectangle(string name, int length, int width) : this(name)
    {
        SetSideLength(0, length); // 设置对边1的长度
        SetSideLength(2, length); // 设置对边3的长度
        SetSideLength(1, width);  // 设置对边2的宽度
        SetSideLength(3, width);  // 设置对边4的宽度
    }

    // 重写 SetSideLength 以确保矩形对边相等
    public override void SetSideLength(int sideIndex, int length)
    {
        // 调用基类方法设置边长
        base.SetSideLength(sideIndex, length);
        // 根据索引，设置对边的长度以保持矩形属性
        int oppositeIndex = (sideIndex + 2) % 4;
        base.SetSideLength(oppositeIndex, length);
    }

    // 重写 Area 方法
    public override double Area()
    {
        // 面积 = 长 * 宽
        return GetSideLength(0) * GetSideLength(1);
    }
}
```

在 `Rectangle` 的构造函数中，`: base(4, name)` 调用了基类 `Polygon` 的构造函数，传入边数（4）和名称。`SetSideLength` 方法被重写，以确保当你设置一条边的长度时，它的对边也会被自动设置为相同的长度，从而维持矩形的形状。

### 创建派生类：Triangle

我们再创建一个 `Triangle`（三角形）类。

```csharp
public class Triangle : Polygon
{
    public Triangle(string name) : base(3, name)
    {
    }

    // 重写 Area 方法，使用海伦公式计算面积
    public override double Area()
    {
        double a = GetSideLength(0);
        double b = GetSideLength(1);
        double c = GetSideLength(2);
        double s = Perimeter / 2.0; // 半周长
        // 海伦公式: Area = sqrt(s * (s-a) * (s-b) * (s-c))
        return Math.Sqrt(s * (s - a) * (s - b) * (s - c));
    }
}
```

### 多态的力量

多态允许我们将派生类对象视为其基类类型。这意味着我们可以创建一个基类类型的集合（如 `List<Polygon>`），其中可以包含任何派生类（`Rectangle`, `Triangle`）的对象。当调用一个虚方法（如 `Area()`）时，C# 会自动调用对象实际类型的重写版本。


![](img/6fd630df18ef8be921ebbea0afd081fa_58.png)

![](img/6fd630df18ef8be921ebbea0afd081fa_60.png)


![](img/6fd630df18ef8be921ebbea0afd081fa_62.png)

![](img/6fd630df18ef8be921ebbea0afd081fa_64.png)

```csharp
// 创建一个多边形列表
List<Polygon> shapes = new List<Polygon>();
// 添加不同类型的多边形
shapes.Add(new Rectangle("我的矩形", 5, 3));
shapes.Add(new Triangle("我的三角形"));
// 设置三角形的边长（3-4-5直角三角形）
shapes[1].SetSideLength(0, 3);
shapes[1].SetSideLength(1, 4);
shapes[1].SetSideLength(2, 5);
// 遍历列表，多态确保调用正确的 Area 方法
foreach (Polygon shape in shapes)
{
    Console.WriteLine(shape.ToString());
    // 输出：
    // 我的矩形: 面积 = 15.00, 周长 = 16
    // 我的三角形: 面积 = 6.00, 周长 = 12
}
```

即使循环变量 `shape` 的类型是 `Polygon`，运行时调用的是 `Rectangle.Area()` 或 `Triangle.Area()`，这就是多态的行为。

---

## 总结

本节课中我们一起学习了C#中两个关键的高级主题。

首先，我们探讨了**空值处理**，学习了如何使用空条件运算符 (`?.`)、空合并运算符 (`??`) 和可空引用类型 (`?`) 来安全地处理可能为 `null` 的对象，从而避免程序崩溃。

![](img/6fd630df18ef8be921ebbea0afd081fa_66.png)

![](img/6fd630df18ef8be921ebbea0afd081fa_68.png)

接着，我们深入研究了**继承与多态**。我们创建了一个 `Polygon` 基类，并从中派生出 `Rectangle` 和 `Triangle` 类。通过将方法标记为 `virtual` 并在派生类中使用 `override` 进行重写，我们实现了多态行为。这使得我们可以用基类类型统一处理不同的派生类对象，同时确保调用的是各自特定的实现。

![](img/6fd630df18ef8be921ebbea0afd081fa_70.png)

掌握这些概念对于构建结构良好、可扩展且健壮的C#应用程序至关重要。在下一讲中，我们将继续探索接口、泛型等更多面向对象的高级特性。