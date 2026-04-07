# 002：C#基础入门

![](img/60540582cab1dde6b733b6c1b0d4c6fb_0.png)

![](img/60540582cab1dde6b733b6c1b0d4c6fb_2.png)

![](img/60540582cab1dde6b733b6c1b0d4c6fb_4.png)

![](img/60540582cab1dde6b733b6c1b0d4c6fb_6.png)

在本节课中，我们将要学习C#编程语言的基础知识。课程内容基于教材的前14章，涵盖了从变量、数据类型、控制流到方法等核心概念。如果你之前没有接触过C#，本节将为你打下坚实的基础。

![](img/60540582cab1dde6b733b6c1b0d4c6fb_8.png)

![](img/60540582cab1dde6b733b6c1b0d4c6fb_9.png)

![](img/60540582cab1dde6b733b6c1b0d4c6fb_11.png)

![](img/60540582cab1dde6b733b6c1b0d4c6fb_13.png)

![](img/60540582cab1dde6b733b6c1b0d4c6fb_15.png)

![](img/60540582cab1dde6b733b6c1b0d4c6fb_17.png)

![](img/60540582cab1dde6b733b6c1b0d4c6fb_19.png)

## 概述与课程结构

![](img/60540582cab1dde6b733b6c1b0d4c6fb_21.png)

![](img/60540582cab1dde6b733b6c1b0d4c6fb_23.png)

![](img/60540582cab1dde6b733b6c1b0d4c6fb_25.png)

![](img/60540582cab1dde6b733b6c1b0d4c6fb_26.png)

![](img/60540582cab1dde6b733b6c1b0d4c6fb_28.png)

上一节我们介绍了课程的整体安排，本节中我们来看看C#语言的具体基础内容。课程将快速浏览C#的基础语法，这些内容与你可能学过的C++有诸多相似之处，但C#也提供了许多更便捷的特性。

![](img/60540582cab1dde6b733b6c1b0d4c6fb_30.png)

![](img/60540582cab1dde6b733b6c1b0d4c6fb_32.png)

![](img/60540582cab1dde6b733b6c1b0d4c6fb_33.png)

以下是本课程后续几周的核心内容大纲：
*   **基础语法**：变量、类型、运算符、控制流（if/else, switch, 循环）、数组和方法。
*   **内存管理**：简要介绍C#作为托管语言如何自动管理内存。
*   **图形用户界面**：使用C#强大的拖拽功能构建窗体应用程序。
*   **面向对象编程**：类、继承、多态、接口等。
*   **高级主题**：委托、事件、Lambda表达式、文件操作等。

![](img/60540582cab1dde6b733b6c1b0d4c6fb_35.png)

![](img/60540582cab1dde6b733b6c1b0d4c6fb_36.png)

![](img/60540582cab1dde6b733b6c1b0d4c6fb_38.png)

![](img/60540582cab1dde6b733b6c1b0d4c6fb_40.png)

## 变量与基本类型

![](img/60540582cab1dde6b733b6c1b0d4c6fb_42.png)

![](img/60540582cab1dde6b733b6c1b0d4c6fb_44.png)

![](img/60540582cab1dde6b733b6c1b0d4c6fb_46.png)

在C#中声明和使用变量与C++非常相似。C#提供了一系列基本（原始）类型，并且拥有方便的`var`关键字进行类型推断。

![](img/60540582cab1dde6b733b6c1b0d4c6fb_48.png)

![](img/60540582cab1dde6b733b6c1b0d4c6fb_50.png)

以下是声明不同类型变量的示例：
```csharp
double someNumber = 4.2;
int anotherNumber = 1;
string name = “Eric”;
```
你可以使用加号`+`进行字符串连接。当字符串与数字使用`+`时，C#会自动将数字转换为字符串并进行拼接。
```csharp
Console.WriteLine(name + anotherNumber); // 输出 “Eric1”
```
更现代和推荐的方式是使用**字符串插值**，它通过在字符串前加`$`符号，并用花括号`{}`包裹变量来实现，使代码更清晰易读。
```csharp
int creditsEarned = 9;
int creditsRequired = 60;
Console.WriteLine($“Eric has {creditsEarned} credits out of {creditsRequired} required for degree.”);
```
对于基本类型，C#还提供了对应的包装类（如`Double`, `Int32`），这些类包含有用的常量和静态方法。
```csharp
double piValue = Math.PI;
Console.WriteLine($“The value of pi is {piValue}”);
```
`var`关键字允许编译器根据所赋的值推断变量类型。一旦推断完成，类型就固定了，这与Python等动态类型语言不同。
```csharp
var inferredInt = 2; // 编译器推断为 int
var lastName = “Charnasky”; // 编译器推断为 string
// inferredInt = “hello”; // 错误：无法将类型’string’隐式转换为’int’
```

![](img/60540582cab1dde6b733b6c1b0d4c6fb_52.png)

![](img/60540582cab1dde6b733b6c1b0d4c6fb_54.png)

![](img/60540582cab1dde6b733b6c1b0d4c6fb_56.png)

![](img/60540582cab1dde6b733b6c1b0d4c6fb_58.png)

![](img/60540582cab1dde6b733b6c1b0d4c6fb_60.png)

![](img/60540582cab1dde6b733b6c1b0d4c6fb_62.png)

![](img/60540582cab1dde6b733b6c1b0d4c6fb_63.png)

![](img/60540582cab1dde6b733b6c1b0d4c6fb_65.png)

## 控制台输入与类型转换

![](img/60540582cab1dde6b733b6c1b0d4c6fb_67.png)

![](img/60540582cab1dde6b733b6c1b0d4c6fb_69.png)

![](img/60540582cab1dde6b733b6c1b0d4c6fb_71.png)

![](img/60540582cab1dde6b733b6c1b0d4c6fb_73.png)

![](img/60540582cab1dde6b733b6c1b0d4c6fb_74.png)

![](img/60540582cab1dde6b733b6c1b0d4c6fb_76.png)

从控制台获取的输入始终是字符串类型。若要进行数学运算，需要使用`Parse`方法将其转换为数值类型。

![](img/60540582cab1dde6b733b6c1b0d4c6fb_78.png)

![](img/60540582cab1dde6b733b6c1b0d4c6fb_80.png)

![](img/60540582cab1dde6b733b6c1b0d4c6fb_82.png)

以下是获取用户输入并计算的示例：
```csharp
Console.Write(“Please enter servings of salad: “);
string input = Console.ReadLine();
int servingsOfSalad = int.Parse(input); // 将字符串转换为整数
Console.WriteLine($“Go eat your {servingsOfSalad} servings of salad.”);
```
更安全的做法是使用`TryParse`方法，它可以避免在输入格式错误时导致程序崩溃。我们将在讨论异常处理时详细介绍它。

![](img/60540582cab1dde6b733b6c1b0d4c6fb_84.png)

![](img/60540582cab1dde6b733b6c1b0d4c6fb_86.png)

![](img/60540582cab1dde6b733b6c1b0d4c6fb_88.png)

## 运算符与数学运算

![](img/60540582cab1dde6b733b6c1b0d4c6fb_90.png)

![](img/60540582cab1dde6b733b6c1b0d4c6fb_92.png)

![](img/60540582cab1dde6b733b6c1b0d4c6fb_94.png)

![](img/60540582cab1dde6b733b6c1b0d4c6fb_95.png)

![](img/60540582cab1dde6b733b6c1b0d4c6fb_97.png)

![](img/60540582cab1dde6b733b6c1b0d4c6fb_99.png)

![](img/60540582cab1dde6b733b6c1b0d4c6fb_101.png)

![](img/60540582cab1dde6b733b6c1b0d4c6fb_103.png)

![](img/60540582cab1dde6b733b6c1b0d4c6fb_105.png)

![](img/60540582cab1dde6b733b6c1b0d4c6fb_107.png)

C#中的算术运算符与C++一致。需要注意的是整数除法：两个整数相除结果仍是整数，小数部分会被截断。
```csharp
int result1 = 5 / 2; // 结果是 2，不是 2.5
double result2 = 5.0 / 2; // 结果是 2.5，因为其中一个操作数是double
```
运算符的优先级遵循标准的数学规则（括号、乘除、加减）。当你不确定时，使用括号来明确运算顺序总是个好主意。
C#也提供了`Math`类来进行更复杂的数学运算，例如求幂、平方根、三角函数等。
```csharp
double power = Math.Pow(2, 5); // 计算 2 的 5 次方，结果是 32
```
需要注意，`^`符号在C#中是按位异或运算符，而不是求幂运算符。

![](img/60540582cab1dde6b733b6c1b0d4c6fb_109.png)

![](img/60540582cab1dde6b733b6c1b0d4c6fb_111.png)

![](img/60540582cab1dde6b733b6c1b0d4c6fb_113.png)

![](img/60540582cab1dde6b733b6c1b0d4c6fb_115.png)

![](img/60540582cab1dde6b733b6c1b0d4c6fb_117.png)

![](img/60540582cab1dde6b733b6c1b0d4c6fb_119.png)

![](img/60540582cab1dde6b733b6c1b0d4c6fb_121.png)

![](img/60540582cab1dde6b733b6c1b0d4c6fb_123.png)

## 流程控制：条件与循环

`if-else`语句、`switch`语句以及各种循环（`for`, `while`, `do-while`）在C#中的工作方式与C++几乎完全相同。

![](img/60540582cab1dde6b733b6c1b0d4c6fb_125.png)

![](img/60540582cab1dde6b733b6c1b0d4c6fb_126.png)

![](img/60540582cab1dde6b733b6c1b0d4c6fb_128.png)

![](img/60540582cab1dde6b733b6c1b0d4c6fb_130.png)

![](img/60540582cab1dde6b733b6c1b0d4c6fb_132.png)

一个基本的`if-else`示例：
```csharp
if (servingsOfSalad > 7)
{
    Console.WriteLine(“Whoa Nelly, that’s too much salad!”);
}
else
{
    Console.WriteLine(“Good job.”);
}
```
**强烈建议始终使用花括号 `{}`**，即使循环体或条件体只有一行代码。这可以避免因代码格式错误导致的逻辑bug，历史上甚至因此导致过严重的安全漏洞。
对于多条件判断，可以使用逻辑运算符 `&&` (与)、`||` (或)、`!` (非)。
```csharp
bool tooMuchSalad = servingsOfSalad > 7;
string name = “Eric Charnasky”;
if (tooMuchSalad && name.Equals(“Eric Charnasky”, StringComparison.OrdinalIgnoreCase))
{
    Console.WriteLine(“Eric, you really shouldn’t eat that much salad.”);
}
```
注意，比较字符串时，使用 `.Equals()` 方法并指定 `StringComparison.OrdinalIgnoreCase` 可以方便地进行不区分大小写的比较。
`switch`语句在C#中功能更强大，可以基于字符串进行判断。
```csharp
switch (lastName)
{
    case “Charnasky”:
        Console.WriteLine(“You are my relative.”);
        break;
    case “Smith”:
        Console.WriteLine(“You are related to 2 billion people.”);
        break;
    default:
        Console.WriteLine(“Unknown relatives.”);
        break;
}
```
此外，C#还引入了更简洁的**switch表达式**，它可以返回值并避免繁琐的`break`语句。
循环的语法与C++一致，`for`循环、`while`循环和`do-while`循环都可以使用。`break`和`continue`语句的作用也相同。

![](img/60540582cab1dde6b733b6c1b0d4c6fb_134.png)

![](img/60540582cab1dde6b733b6c1b0d4c6fb_135.png)

![](img/60540582cab1dde6b733b6c1b0d4c6fb_137.png)

![](img/60540582cab1dde6b733b6c1b0d4c6fb_139.png)

## 数组

![](img/60540582cab1dde6b733b6c1b0d4c6fb_141.png)

![](img/60540582cab1dde6b733b6c1b0d4c6fb_143.png)

![](img/60540582cab1dde6b733b6c1b0d4c6fb_145.png)

数组在C#中是固定长度的，但其使用比C++更方便，因为你可以直接通过`.Length`属性获取数组长度。

![](img/60540582cab1dde6b733b6c1b0d4c6fb_147.png)

![](img/60540582cab1dde6b733b6c1b0d4c6fb_148.png)

![](img/60540582cab1dde6b733b6c1b0d4c6fb_150.png)

以下是声明和初始化数组的几种方式：
```csharp
// 方式1：先声明，后逐个赋值
int[] scores = new int[5];
scores[0] = 100;
scores[1] = 95;
// … 赋值 scores[2], scores[3], scores[4]

![](img/60540582cab1dde6b733b6c1b0d4c6fb_152.png)

![](img/60540582cab1dde6b733b6c1b0d4c6fb_154.png)

![](img/60540582cab1dde6b733b6c1b0d4c6fb_156.png)

![](img/60540582cab1dde6b733b6c1b0d4c6fb_158.png)

![](img/60540582cab1dde6b733b6c1b0d4c6fb_160.png)

// 方式2：使用初始化器语法
int[] fasterScores = new int[] { 100, 95, 90, 85, 80 };
// 或者更简洁的写法
int[] fastestScores = { 100, 95, 90, 85, 80 };
```
使用`for`循环遍历数组时，可以利用`.Length`属性：
```csharp
for (int index = 0; index < fastestScores.Length; index++)
{
    Console.WriteLine($“Score at index {index} is {fastestScores[index]}”);
}
```
C#还提供了更安全的**范围索引器**，例如 `^1` 表示最后一个元素，避免了手动计算 `array.Length – 1`。
此外，`foreach`循环提供了一种更简洁、只读的方式来遍历数组或集合中的每个元素。
```csharp
foreach (int score in fastestScores)
{
    Console.WriteLine(score);
}
```
与C++一样，访问数组边界之外的元素会引发 `IndexOutOfRangeException` 异常，导致程序崩溃，这是一种安全机制。

![](img/60540582cab1dde6b733b6c1b0d4c6fb_162.png)

![](img/60540582cab1dde6b733b6c1b0d4c6fb_164.png)

## 方法（函数）

方法的定义和调用在C#中非常直观。编译器会扫描整个文件来解析方法，因此不需要像C++那样必须先声明后定义。

![](img/60540582cab1dde6b733b6c1b0d4c6fb_166.png)

![](img/60540582cab1dde6b733b6c1b0d4c6fb_168.png)

![](img/60540582cab1dde6b733b6c1b0d4c6fb_170.png)

![](img/60540582cab1dde6b733b6c1b0d4c6fb_172.png)

![](img/60540582cab1dde6b733b6c1b0d4c6fb_174.png)

一个简单的方法示例：
```csharp
void PrintSomething()
{
    Console.WriteLine(“Let me out!”);
}
// 在Main中调用
for (int i = 0; i < 5; i++)
{
    PrintSomething();
}
```
方法可以接收参数和返回值：
```csharp
string GetFavoriteColor()
{
    return “blue”;
}
void SayHello(string name = “no name”) // 参数带有默认值
{
    Console.WriteLine($“Hi there {name}”);
}
// 调用
string color = GetFavoriteColor();
Console.WriteLine($“Eric’s favorite color is {color}”);
SayHello(“Alice”);
SayHello(); // 使用默认参数，输出 “Hi there no name”
```
对于非常简单的方法，可以使用**表达式主体定义**来使代码更紧凑。它使用 `=>` 符号来替代方法体和 `return` 语句。
```csharp
int AddThreeNumbers(int first, int second, int third) => first + second + third;
// 等价于：
// int AddThreeNumbers(int first, int second, int third)
// {
//     return first + second + third;
// }
```

## 项目实践：联邦所得税计算器

现在，我们将运用以上知识来创建第一个“游戏”——一个联邦所得税计算器。这个程序将模拟计算美国阶梯税率下的应缴税款。

![](img/60540582cab1dde6b733b6c1b0d4c6fb_176.png)

![](img/60540582cab1dde6b733b6c1b0d4c6fb_177.png)

![](img/60540582cab1dde6b733b6c1b0d4c6fb_179.png)

### 项目要求
1.  **获取总收入**：提示用户输入所有W-2收入（代表工资收入），并持续循环直到用户输入完成。将所有收入相加得到**总收入**。
2.  **获取扣除额**：提示用户输入可抵扣项（如慈善捐款），持续循环直到输入完成。计算**扣除总额**。
3.  **计算调整后总收入**：**调整后总收入 = 总收入 – MAX(扣除总额，标准扣除额)**。2023年的标准扣除额为 **$13,850**。
4.  **计算应纳税额**：根据2023年税率表，采用阶梯税率计算：
    *   收入在 $0 – $11,000 的部分，税率为 10%
    *   $11,001 – $44,725 的部分，税率为 12%
    *   $44,726 – $95,375 的部分，税率为 22%
    *   $95,376 – $182,100 的部分，税率为 24%
    *   $182,101 – $231,250 的部分，税率为 32%
    *   $231,251 – $578,125 的部分，税率为 35%
    *   $578,126 以上的部分，税率为 37%
    *   **注意**：计算时需逐级计算，即仅对超过每一级门槛的部分按该级税率征税。
5.  **输出结果**：
    *   显示每一档税率对应的应纳税额。
    *   显示**应纳税总额**。
    *   显示应纳税总额占**调整后总收入**的百分比。
    *   显示应纳税总额占**总收入**的百分比。

![](img/60540582cab1dde6b733b6c1b0d4c6fb_181.png)

![](img/60540582cab1dde6b733b6c1b0d4c6fb_183.png)

![](img/60540582cab1dde6b733b6c1b0d4c6fb_185.png)

![](img/60540582cab1dde6b733b6c1b0d4c6fb_187.png)

![](img/60540582cab1dde6b733b6c1b0d4c6fb_189.png)

![](img/60540582cab1dde6b733b6c1b0d4c6fb_191.png)

### 实现思路
核心逻辑是一系列`if-else if`判断，从高收入级别向低收入级别计算。对于每一级，判断调整后总收入是否超过该级别的下限，如果超过，则对该级区间内的收入（即 `收入 – 本级下限`，但不超过本级上限）应用相应税率。

## 总结

![](img/60540582cab1dde6b733b6c1b0d4c6fb_193.png)

本节课中我们一起学习了C#编程语言的基础核心概念。我们介绍了如何声明变量和使用基本数据类型，如何进行控制台输入输出及类型转换，掌握了各种运算符和数学运算的规则。我们还深入探讨了控制程序流程的条件语句和循环结构，学习了数组的声明、初始化和遍历方法。最后，我们了解了如何定义和调用方法，包括使用参数、返回值和表达式主体定义。这些知识是进行C#游戏开发乃至任何C#应用程序开发的基石。请务必通过实践项目来巩固这些概念。