# 004：分支结构（第二部分） 🧭

![](img/aca4d2d45dff76f8d9b0ad6480cab151_0.png)

在本节课中，我们将继续学习C++中的分支结构，重点探讨如何利用`if-else`语句处理数值范围、使用逻辑运算符组合条件，以及一些关于字符串操作和浮点数比较的实用技巧。上一节我们介绍了基本的`if`和`switch`语句，本节中我们来看看如何更灵活地运用它们。

## 概述

本节课我们将学习如何将百分比分数转换为字母等级、计算关税成本、检查字符串内容以及安全地比较浮点数。这些练习将帮助我们巩固对分支结构和逻辑运算的理解。

---

## 将分数转换为字母等级 📊

一个常见的应用是将百分制分数转换为字母等级（A, B, C等）。我们可以通过一系列`if-else if`语句来实现，每个语句检查一个分数范围。

以下是实现此功能的步骤：

1.  声明一个`double`类型的变量来存储百分比分数。
2.  提示用户输入分数。
3.  使用`if-else if`链检查分数落入哪个等级范围。
4.  输出对应的字母等级。

![](img/aca4d2d45dff76f8d9b0ad6480cab151_2.png)

**核心代码示例：**
```cpp
double percentage;
cout << "Enter your grade percentage: ";
cin >> percentage;

if (percentage >= 94) {
    cout << "You have an A." << endl;
}
else if (percentage >= 90) { // 隐含条件：percentage < 94
    cout << "You have an A-." << endl;
}
// ... 继续为 B+, B, B-, C+, C, C-, D+, D 添加条件
else {
    cout << "You fail." << endl; // 默认情况
}
```
**关键点：** 通过按顺序（从高分到低分）检查条件，我们为每个`else if`语句创建了隐式范围。例如，只有当分数不满足`>=94`时，程序才会检查`>=90`，这等同于检查`分数 < 94 && 分数 >= 90`。

---

![](img/aca4d2d45dff76f8d9b0ad6480cab151_4.png)

![](img/aca4d2d45dff76f8d9b0ad6480cab151_5.png)

![](img/aca4d2d45dff76f8d9b0ad6480cab151_7.png)

![](img/aca4d2d45dff76f8d9b0ad6480cab151_8.png)

## 计算关税成本 💰

假设我们需要根据订单金额和原产国计算关税。这涉及到多个条件的组合判断。

![](img/aca4d2d45dff76f8d9b0ad6480cab151_10.png)

![](img/aca4d2d45dff76f8d9b0ad6480cab151_12.png)

以下是实现此功能的步骤：

1.  定义常量（如免税订单上限`TARIFF_ORDER_MINIMUM`）和变量（订单金额、原产国、关税税率）。
2.  获取用户输入的订单金额和原产国。
3.  使用`if-else if`语句判断适用的关税规则（例如，小额订单免税、本国产品免税、特定国家税率）。
4.  计算并输出关税成本。

![](img/aca4d2d45dff76f8d9b0ad6480cab151_14.png)

![](img/aca4d2d45dff76f8d9b0ad6480cab151_15.png)

![](img/aca4d2d45dff76f8d9b0ad6480cab151_16.png)

**核心代码示例：**
```cpp
const double TARIFF_ORDER_MINIMUM = 800.0;
const double TARIFF_RATE_INDIA = 0.25;
const double TARIFF_RATE_BRAZIL = 0.50;

![](img/aca4d2d45dff76f8d9b0ad6480cab151_18.png)

![](img/aca4d2d45dff76f8d9b0ad6480cab151_20.png)

![](img/aca4d2d45dff76f8d9b0ad6480cab151_22.png)

![](img/aca4d2d45dff76f8d9b0ad6480cab151_24.png)

![](img/aca4d2d45dff76f8d9b0ad6480cab151_25.png)

double orderCost, tariffCost = 0.0;
string countryOfOrigin;

![](img/aca4d2d45dff76f8d9b0ad6480cab151_27.png)

// ... 获取用户输入

if (orderCost <= TARIFF_ORDER_MINIMUM) {
    tariffCost = 0.0;
}
else if (countryOfOrigin == "USA") {
    tariffCost = 0.0;
}
else if (countryOfOrigin == "India") {
    tariffCost = orderCost * TARIFF_RATE_INDIA;
}
else if (countryOfOrigin == "Brazil") {
    tariffCost = orderCost * TARIFF_RATE_BRAZIL;
}
// ... 可以添加更多国家的判断

![](img/aca4d2d45dff76f8d9b0ad6480cab151_29.png)

![](img/aca4d2d45dff76f8d9b0ad6480cab151_31.png)

![](img/aca4d2d45dff76f8d9b0ad6480cab151_33.png)

cout << "Your tariff cost is $" << tariffCost << endl;
```
**关键点：** 使用常量便于集中管理可能变化的数值（如税率）。逻辑运算符`||`（或）可用于检查无效输入，例如`if (percentage < 0 || percentage > 100)`。

![](img/aca4d2d45dff76f8d9b0ad6480cab151_35.png)

![](img/aca4d2d45dff76f8d9b0ad6480cab151_36.png)

---

## 条件（三元）运算符 ⚡

条件运算符 (`? :`) 提供了一种简洁的内联方式来表达简单的`if-else`赋值逻辑。其语法为：`条件 ? 表达式1 : 表达式2`。如果条件为真，整个表达式取`表达式1`的值，否则取`表达式2`的值。

![](img/aca4d2d45dff76f8d9b0ad6480cab151_38.png)

![](img/aca4d2d45dff76f8d9b0ad6480cab151_40.png)

**核心公式：**
```
变量 = (条件) ? 值1 : 值2;
```

![](img/aca4d2d45dff76f8d9b0ad6480cab151_42.png)

![](img/aca4d2d45dff76f8d9b0ad6480cab151_44.png)

**代码示例对比：**
```cpp
// 使用 if-else
if (orderCost <= TARIFF_ORDER_MINIMUM) {
    tariffCost = 0.0;
} else {
    tariffCost = orderCost * someRate;
}

![](img/aca4d2d45dff76f8d9b0ad6480cab151_46.png)

![](img/aca4d2d45dff76f8d9b0ad6480cab151_48.png)

![](img/aca4d2d45dff76f8d9b0ad6480cab151_50.png)

// 使用条件运算符实现相同功能
tariffCost = (orderCost <= TARIFF_ORDER_MINIMUM) ? 0.0 : (orderCost * someRate);
```
**注意：** 虽然条件运算符代码更紧凑，但嵌套或复杂的条件会降低可读性。对于初学者，清晰的`if-else`语句通常是更好的选择。**务必始终使用花括号`{}`包裹`if/else`下的代码块**，以避免因遗漏导致的逻辑错误。

![](img/aca4d2d45dff76f8d9b0ad6480cab151_52.png)

---

![](img/aca4d2d45dff76f8d9b0ad6480cab151_54.png)

## 字符串操作 🔤

`string`类提供了多种方法来检查和操作文本。

![](img/aca4d2d45dff76f8d9b0ad6480cab151_56.png)

![](img/aca4d2d45dff76f8d9b0ad6480cab151_58.png)

![](img/aca4d2d45dff76f8d9b0ad6480cab151_59.png)

### 查找子字符串
使用`.find()`方法可以查找字符或子串在字符串中的位置。如果未找到，它会返回一个特殊的常量`string::npos`。

**核心代码示例：**
```cpp
string email = "user@example.com";
size_t atPosition = email.find('@'); // 查找'@'符号的位置

if (atPosition == string::npos) {
    cout << "Invalid email: missing '@'" << endl;
} else {
    string username = email.substr(0, atPosition); // 从开始到'@'之前
    string domain = email.substr(atPosition + 1); // 从'@'之后到结尾
    cout << "Username: " << username << ", Domain: " << domain << endl;
}
```

### 替换字符串内容
使用`.replace()`方法可以替换字符串中的一部分。

**核心代码示例：**
```cpp
string message = "apple";
// 将位置1开始的2个字符（"pp"）替换为"bb"
message.replace(1, 2, "bb");
cout << message << endl; // 输出: abble
```
**注意：** 在没有循环的情况下进行全局查找和替换（如将所有‘a’替换为‘b’）比较繁琐，我们将在学习循环后更高效地处理。

---

![](img/aca4d2d45dff76f8d9b0ad6480cab151_61.png)

![](img/aca4d2d45dff76f8d9b0ad6480cab151_63.png)

## 浮点数比较的注意事项 ⚖️

![](img/aca4d2d45dff76f8d9b0ad6480cab151_65.png)

由于浮点数在计算机中以二进制近似存储，直接使用`==`比较两个计算出的浮点数可能因微小的舍入误差而失败。

![](img/aca4d2d45dff76f8d9b0ad6480cab151_67.png)

![](img/aca4d2d45dff76f8d9b0ad6480cab151_69.png)

![](img/aca4d2d45dff76f8d9b0ad6480cab151_71.png)

**安全做法：** 不检查是否“完全相等”，而是检查两者的差值是否小于一个极小的容差值（如`0.000001`）。

![](img/aca4d2d45dff76f8d9b0ad6480cab151_73.png)

![](img/aca4d2d45dff76f8d9b0ad6480cab151_75.png)

![](img/aca4d2d45dff76f8d9b0ad6480cab151_77.png)

![](img/aca4d2d45dff76f8d9b0ad6480cab151_79.png)

![](img/aca4d2d45dff76f8d9b0ad6480cab151_81.png)

**核心公式：**
```
if (fabs(a - b) < EPSILON) {
    // 认为 a 和 b 相等
}
```
**代码示例：**
```cpp
#include <cmath> // 用于 fabs
const double EPSILON = 0.000001;
double result = 1.0 / 3.0;
double expected = 0.3333333333333333;

![](img/aca4d2d45dff76f8d9b0ad6480cab151_83.png)

// 不安全的比较
// if (result == expected) ... 

![](img/aca4d2d45dff76f8d9b0ad6480cab151_85.png)

![](img/aca4d2d45dff76f8d9b0ad6480cab151_87.png)

// 安全的比较
if (fabs(result - expected) < EPSILON) {
    cout << "The result is approximately one third." << endl;
}
```
**关键点：** `fabs()`函数用于计算浮点数的绝对值。`EPSILON`的值根据你所需的精度而定。

![](img/aca4d2d45dff76f8d9b0ad6480cab151_89.png)

![](img/aca4d2d45dff76f8d9b0ad6480cab151_91.png)

---

![](img/aca4d2d45dff76f8d9b0ad6480cab151_93.png)

![](img/aca4d2d45dff76f8d9b0ad6480cab151_95.png)

![](img/aca4d2d45dff76f8d9b0ad6480cab151_97.png)

## 短路求值 🔌

![](img/aca4d2d45dff76f8d9b0ad6480cab151_99.png)

![](img/aca4d2d45dff76f8d9b0ad6480cab151_101.png)

![](img/aca4d2d45dff76f8d9b0ad6480cab151_103.png)

![](img/aca4d2d45dff76f8d9b0ad6480cab151_105.png)

C++在进行逻辑与(`&&`)和逻辑或(`||`)运算时采用“短路求值”。这意味着：
*   对于`表达式1 && 表达式2`，如果`表达式1`为`false`，则整个表达式已确定为`false`，`表达式2`将**不会被执行**。
*   对于`表达式1 || 表达式2`，如果`表达式1`为`true`，则整个表达式已确定为`true`，`表达式2`将**不会被执行**。

![](img/aca4d2d45dff76f8d9b0ad6480cab151_107.png)

这可以提高效率，并在某些情况下避免错误（例如，当`表达式2`依赖于`表达式1`为真时）。

![](img/aca4d2d45dff76f8d9b0ad6480cab151_109.png)

![](img/aca4d2d45dff76f8d9b0ad6480cab151_111.png)

![](img/aca4d2d45dff76f8d9b0ad6480cab151_113.png)

**代码示例：**
```cpp
int x = 0;
if ( (x != 0) && (10 / x > 2) ) { // 如果 x 为 0，第一部分为 false，第二部分不会执行，避免了除以零的错误。
    // ...
}
```

![](img/aca4d2d45dff76f8d9b0ad6480cab151_115.png)

---

![](img/aca4d2d45dff76f8d9b0ad6480cab151_117.png)

![](img/aca4d2d45dff76f8d9b0ad6480cab151_118.png)

![](img/aca4d2d45dff76f8d9b0ad6480cab151_120.png)

![](img/aca4d2d45dff76f8d9b0ad6480cab151_122.png)

## 总结

本节课中我们一起学习了：
*   使用`if-else if`链处理**数值范围**，例如将分数转换为等级。
*   结合**逻辑运算符**和**常量**来构建更复杂的条件判断，如关税计算。
*   认识了简洁但需谨慎使用的**条件（三元）运算符** (`? :`)。
*   进行了基本的**字符串操作**，包括查找(`.find()`)和替换(`.replace()`)。
*   理解了直接比较**浮点数**的风险，并学会了通过判断差值是否小于容错值来进行安全比较。
*   了解了逻辑运算中的**短路求值**特性及其作用。

![](img/aca4d2d45dff76f8d9b0ad6480cab151_124.png)

![](img/aca4d2d45dff76f8d9b0ad6480cab151_126.png)

这些概念是构建更复杂程序逻辑的基础。请务必通过教材练习和实验来巩固理解。如果你在完成作业时遇到困难，请及时向讲师、助教或辅导中心寻求帮助。