# 003：面向对象编程-part1


![](img/afbf3e8a278ff198478d4e5c0eb42c15_2.png)

在本节课中，我们将学习面向对象编程的基础知识，并利用这些知识来改进我们的税务计算器项目。我们将创建一个`Rectangle`类，学习如何封装数据、定义属性和方法，并探索如何在图形用户界面中动态地使用对象。

---

![](img/afbf3e8a278ff198478d4e5c0eb42c15_4.png)

![](img/afbf3e8a278ff198478d4e5c0eb42c15_6.png)

## 项目回顾与改进




上一节我们完成了基于控制台的税务计算器。本节中，我们将把它改造成一个图形用户界面程序，并在这个过程中引入面向对象的概念。






首先，我们创建了一个新的Windows窗体应用程序项目。界面上包含用于输入收入和扣除额的文本框、对应的标签以及操作按钮。


以下是核心的类级变量，用于在整个窗体类中跟踪总收入、总扣除额等数据：
```csharp
private int grossIncome = 0;
private int totalDeductions = 0;
private int deductionsClaimed = 0;
```



当用户点击“添加收入”按钮时，程序会从文本框中读取数值，更新总收入，并重新计算和显示税款。我们使用了一个辅助函数 `UpdateTaxesOwedLabel()` 来集中处理税款计算和标签更新逻辑。


![](img/afbf3e8a278ff198478d4e5c0eb42c15_31.png)

税款计算逻辑与之前项目类似，但使用了三元运算符来简洁地确定应申请的扣除额：
```csharp
deductionsClaimed = (totalDeductions > STANDARD_DEDUCTION) ? totalDeductions : STANDARD_DEDUCTION;
```

为了提升用户体验，我们在每次添加收入或扣除后清空了对应的文本框。

![](img/afbf3e8a278ff198478d4e5c0eb42c15_33.png)

![](img/afbf3e8a278ff198478d4e5c0eb42c15_35.png)

---

![](img/afbf3e8a278ff198478d4e5c0eb42c15_37.png)

![](img/afbf3e8a278ff198478d4e5c0eb42c15_39.png)

## 引入面向对象编程

![](img/afbf3e8a278ff198478d4e5c0eb42c15_41.png)

接下来，我们转向面向对象编程的核心概念。面向对象编程的核心思想是将数据和对数据的操作封装在“类”中。类就像一个蓝图，定义了对象应有的属性和行为。

![](img/afbf3e8a278ff198478d4e5c0eb42c15_43.png)

![](img/afbf3e8a278ff198478d4e5c0eb42c15_45.png)

![](img/afbf3e8a278ff198478d4e5c0eb42c15_47.png)

我们创建了一个名为 `Rectangle` 的类来演示这一概念。

### 定义 `Rectangle` 类

这个类有两个私有属性：`length`（长）和 `width`（宽）。将它们设为私有是为了保护数据的完整性，外部代码不能直接修改它们，必须通过我们提供的公共方法。

```csharp
private int length;
private int width;
```

我们为 `Rectangle` 类定义了一个构造函数，用于在创建对象时初始化长和宽。在构造函数中，我们通过调用 `SetLength` 和 `SetWidth` 方法来确保传入的值有效（例如，不能为负数）。

```csharp
public Rectangle(int length, int width)
{
    SetLength(length);
    SetWidth(width);
}
```


![](img/afbf3e8a278ff198478d4e5c0eb42c15_51.png)

### 公共方法：Getter 和 Setter


为了允许外部代码安全地访问和修改矩形的尺寸，我们提供了公共的 Getter 和 Setter 方法。Setter 方法中包含验证逻辑，确保长和宽不为负。

![](img/afbf3e8a278ff198478d4e5c0eb42c15_55.png)


![](img/afbf3e8a278ff198478d4e5c0eb42c15_57.png)


```csharp
public int GetLength() { return length; }
public void SetLength(int newLength) { length = (newLength < 0) ? 0 : newLength; }
public int GetWidth() { return width; }
public void SetWidth(int newWidth) { width = (newWidth < 0) ? 0 : newWidth; }
```

### 重写 `ToString` 方法和计算属性

为了让 `Rectangle` 对象能输出有意义的字符串描述，我们重写了从 `Object` 类继承的 `ToString` 方法。

```csharp
public override string ToString()
{
    return $"Rectangle: Length={length}, Width={width}";
}
```



![](img/afbf3e8a278ff198478d4e5c0eb42c15_65.png)

此外，我们还为矩形定义了计算面积和周长的属性。这里使用了C#的表达式主体属性语法，使代码更简洁。




```csharp
public int Area => length * width; // 计算面积的属性
public int Perimeter => 2 * length + 2 * width; // 计算周长的属性
```

---

## 在GUI中使用 `Rectangle` 类

我们在窗体上添加了文本框、按钮和标签，用于创建和显示 `Rectangle` 对象。

当用户点击“创建矩形”按钮时，程序会：
1.  从文本框中获取输入的长和宽。
2.  使用这些值创建一个新的 `Rectangle` 对象实例。
3.  调用该对象的 `ToString()`、`Area` 和 `Perimeter` 属性，并将结果显示在对应的标签上。

我们还尝试使用了 `TrackBar`（滑块）控件来动态调整矩形的尺寸。通过处理滑块的 `Scroll` 事件，我们可以实时更新 `Rectangle` 对象的属性并刷新显示。

![](img/afbf3e8a278ff198478d4e5c0eb42c15_73.png)

---

![](img/afbf3e8a278ff198478d4e5c0eb42c15_75.png)

![](img/afbf3e8a278ff198478d4e5c0eb42c15_77.png)

![](img/afbf3e8a278ff198478d4e5c0eb42c15_79.png)

![](img/afbf3e8a278ff198478d4e5c0eb42c15_81.png)

![](img/afbf3e8a278ff198478d4e5c0eb42c15_83.png)

![](img/afbf3e8a278ff198478d4e5c0eb42c15_85.png)

## 本节课总结

![](img/afbf3e8a278ff198478d4e5c0eb42c15_87.png)

本节课中我们一起学习了面向对象编程的基础。我们通过创建 `Rectangle` 类，实践了如何将数据（长和宽）和操作数据的方法（设置、获取、计算面积和周长）封装在一起。我们了解了私有成员的保护作用、公共接口的定义、构造函数的用途，以及如何重写 `ToString` 方法。最后，我们将这个类应用到了图形用户界面中，实现了数据的动态绑定和交互。这些概念是构建更复杂、更模块化C#应用程序的基石。