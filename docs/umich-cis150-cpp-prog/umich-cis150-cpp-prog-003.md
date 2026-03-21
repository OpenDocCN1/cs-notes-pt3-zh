# 003：分支结构（第一部分） 🧭

![](img/9e7f2d9c3bb1b18eedf189643cc1c69c_0.png)

在本节课中，我们将学习C++中的分支结构。分支结构允许程序根据不同的条件执行不同的代码块，这是让程序变得“智能”和交互性的关键。我们将从基础的 `if` 和 `else` 语句开始，逐步深入到更复杂的逻辑判断。

![](img/9e7f2d9c3bb1b18eedf189643cc1c69c_2.png)

---

## 概述

![](img/9e7f2d9c3bb1b18eedf189643cc1c69c_4.png)

上一周我们学习了变量和基本运算，但程序只能按固定顺序执行，这显得有些单调。本节我们将引入**分支结构**，它能让程序根据用户输入或计算结果做出决策，执行不同的代码路径。我们将重点学习布尔表达式、`if-else` 语句以及 `switch` 语句。

![](img/9e7f2d9c3bb1b18eedf189643cc1c69c_6.png)

![](img/9e7f2d9c3bb1b18eedf189643cc1c69c_7.png)

---

## 布尔表达式与关系运算符

在C++中，**布尔表达式**是分支判断的基础。它只能产生两个结果：`true`（真）或 `false`（假）。这就像电路中的开关，只有“开”或“关”两种状态。

![](img/9e7f2d9c3bb1b18eedf189643cc1c69c_9.png)

![](img/9e7f2d9c3bb1b18eedf189643cc1c69c_11.png)

![](img/9e7f2d9c3bb1b18eedf189643cc1c69c_13.png)

我们使用**关系运算符**来构建布尔表达式，它们用于比较两个值。

![](img/9e7f2d9c3bb1b18eedf189643cc1c69c_15.png)

以下是核心的关系运算符：
*   **大于**： `>`
*   **小于**： `<`
*   **大于等于**： `>=`
*   **小于等于**： `<=`
*   **等于**： `==` （注意：这是两个等号，用于比较；单个等号 `=` 是赋值运算符）
*   **不等于**： `!=`

![](img/9e7f2d9c3bb1b18eedf189643cc1c69c_17.png)

**示例公式**：
```cpp
moneyInPocket > 10 // 检查口袋里的钱是否大于10
choice == 1         // 检查选择是否等于1
```

![](img/9e7f2d9c3bb1b18eedf189643cc1c69c_19.png)

---

## if-else 语句

![](img/9e7f2d9c3bb1b18eedf189643cc1c69c_21.png)

`if-else` 语句是最基本的分支结构。它允许程序在条件为真时执行一段代码，在条件为假时执行另一段代码。

![](img/9e7f2d9c3bb1b18eedf189643cc1c69c_23.png)

![](img/9e7f2d9c3bb1b18eedf189643cc1c69c_25.png)

![](img/9e7f2d9c3bb1b18eedf189643cc1c69c_26.png)

**基本语法**：
```cpp
if (条件) {
    // 如果条件为 true，则执行这里的代码
} else {
    // 如果条件为 false，则执行这里的代码
}
```

![](img/9e7f2d9c3bb1b18eedf189643cc1c69c_28.png)

![](img/9e7f2d9c3bb1b18eedf189643cc1c69c_30.png)

![](img/9e7f2d9c3bb1b18eedf189643cc1c69c_32.png)

![](img/9e7f2d9c3bb1b18eedf189643cc1c69c_34.png)

![](img/9e7f2d9c3bb1b18eedf189643cc1c69c_36.png)

![](img/9e7f2d9c3bb1b18eedf189643cc1c69c_38.png)

![](img/9e7f2d9c3bb1b18eedf189643cc1c69c_40.png)

![](img/9e7f2d9c3bb1b18eedf189643cc1c69c_42.png)

**代码示例**：根据预算决定午餐
```cpp
double moneyInPocket = 12.0;
if (moneyInPocket > 10) {
    cout << "We can get lunch at Picasso." << endl;
} else {
    cout << "We get ramen noodles." << endl;
}
// 输出：We can get lunch at Picasso.
```

为了让程序更灵活，我们通常会让用户输入变量值：
```cpp
cout << "How much money do you have in your pocket? ";
cin >> moneyInPocket;
// ... 后续的 if-else 判断
```

---

## 使用 else if 处理多个条件

当存在两个以上的可能情况时，可以使用 `else if` 来链接多个条件。这些条件是**互斥**的，即只会执行第一个满足条件的代码块。

**代码示例**：更精细的预算分级
```cpp
if (moneyInPocket > 15) {
    cout << "You can get the whole combo at Picasso." << endl;
} else if (moneyInPocket > 10) {
    cout << "You can get lunch at Picasso." << endl;
} else {
    cout << "We get ramen noodles." << endl;
}
```
**重要提示**：`else if` 链的顺序至关重要。条件应该从最严格到最宽松排列，否则后面的条件可能永远无法执行。

![](img/9e7f2d9c3bb1b18eedf189643cc1c69c_44.png)

---

## switch 语句

![](img/9e7f2d9c3bb1b18eedf189643cc1c69c_46.png)

`switch` 语句是另一种多分支选择结构，特别适用于基于一个变量与多个常量值进行比较的情况。

![](img/9e7f2d9c3bb1b18eedf189643cc1c69c_48.png)

![](img/9e7f2d9c3bb1b18eedf189643cc1c69c_50.png)

**基本语法**：
```cpp
switch (表达式) {
    case 常量值1:
        // 代码块1
        break;
    case 常量值2:
        // 代码块2
        break;
    ...
    default:
        // 默认代码块（可选）
}
```

![](img/9e7f2d9c3bb1b18eedf189643cc1c69c_52.png)

**代码示例**：饮料选择菜单
```cpp
int choice;
cout << "Enter your choice (1-4): ";
cin >> choice;

switch (choice) {
    case 1:
        cout << "You got a Coke." << endl;
        break;
    case 2:
        cout << "You got a Coke Zero." << endl;
        break;
    case 3:
        cout << "You got a Mountain Dew." << endl;
        break;
    case 4:
        cout << "You got a Sprite." << endl;
        break;
    default:
        cout << "Invalid choice, no pop for you." << endl;
}
```
**关键点**：
*   `switch` 的表达式结果必须是整型或字符型（`int`, `char` 等），**不能是字符串（`string`）**。
*   每个 `case` 块末尾的 `break;` 语句至关重要，它用于退出整个 `switch` 结构。如果省略 `break`，程序会继续执行下一个 `case` 的代码，这称为“穿透”（fall-through），有时可利用此特性（如下例），但通常需要避免。

**穿透示例**：同时处理大小写字母
```cpp
char input;
cin >> input;
switch (input) {
    case 'y':
    case 'Y':
        cout << "You said yes!" << endl;
        break;
    // ... 其他 case
}
```

---

## 逻辑运算符

有时我们需要组合多个条件。这时就需要用到**逻辑运算符**。

以下是核心的逻辑运算符：
*   **逻辑与 (AND)**： `&&` （当且仅当两边条件都为真时，整个表达式为真）
*   **逻辑或 (OR)**： `||` （只要一边条件为真，整个表达式就为真）
*   **逻辑非 (NOT)**： `!` （反转布尔值，真变假，假变真）

**真值表示例**：
*   `true && true` 结果为 `true`
*   `true && false` 结果为 `false`
*   `true || false` 结果为 `true`
*   `false || false` 结果为 `false`
*   `!true` 结果为 `false`

**代码示例**：组合条件判断
```cpp
if (moneyInPocket > 10 && choice == 1) {
    cout << "You can afford a Coke at Picasso." << endl;
}

if (input == 'y' || input == 'Y') {
    cout << "Proceed with purchase." << endl;
}

![](img/9e7f2d9c3bb1b18eedf189643cc1c69c_54.png)

if (!isHungry) { // 相当于 if (isHungry == false)
    cout << "Skip lunch." << endl;
}
```

![](img/9e7f2d9c3bb1b18eedf189643cc1c69c_56.png)

![](img/9e7f2d9c3bb1b18eedf189643cc1c69c_58.png)

![](img/9e7f2d9c3bb1b18eedf189643cc1c69c_60.png)

---

![](img/9e7f2d9c3bb1b18eedf189643cc1c69c_62.png)

## 运算符优先级

当表达式中包含算术、关系和逻辑运算符时，C++会按照特定的**优先级**顺序进行计算。

![](img/9e7f2d9c3bb1b18eedf189643cc1c69c_64.png)

以下是简化的优先级顺序（从高到低）：
1.  **括号** `()`：优先级最高，用于明确指定计算顺序。
2.  **算术运算符**：如 `+`, `-`, `*`, `/`, `%`。
3.  **关系运算符**：如 `<`, `>`, `<=`, `>=`。
4.  **相等性运算符**：如 `==`, `!=`。
5.  **逻辑与** `&&`。
6.  **逻辑或** `||`。

**最佳实践**：当表达式变得复杂，尤其是混合使用 `&&` 和 `||` 时，**强烈建议使用括号**来明确指定运算顺序，这能让代码更清晰，避免逻辑错误。

![](img/9e7f2d9c3bb1b18eedf189643cc1c69c_66.png)

**示例**：
```cpp
// 使用括号使意图更清晰
if ( (score > 90) || (age < 18 && parentApproval) ) {
    cout << "Eligible for discount." << endl;
}
```

![](img/9e7f2d9c3bb1b18eedf189643cc1c69c_68.png)

![](img/9e7f2d9c3bb1b18eedf189643cc1c69c_70.png)

![](img/9e7f2d9c3bb1b18eedf189643cc1c69c_71.png)

---

## 项目零介绍：派对规划程序 🎉

现在，我们将运用所学的分支知识来完成第一个项目。这是一个派对规划程序，它会根据客人数量和选择的食物来计算需要购买的数量和总成本。

![](img/9e7f2d9c3bb1b18eedf189643cc1c69c_73.png)

![](img/9e7f2d9c3bb1b18eedf189643cc1c69c_75.png)

![](img/9e7f2d9c3bb1b18eedf189643cc1c69c_76.png)

![](img/9e7f2d9c3bb1b18eedf189643cc1c69c_77.png)

![](img/9e7f2d9c3bb1b18eedf189643cc1c69c_79.png)

![](img/9e7f2d9c3bb1b18eedf189643cc1c69c_81.png)

以下是项目要求：
1.  询问用户有多少客人（记得包括主人自己）。
2.  提供三种食物选项供用户选择（例如：蛋糕、披萨、汽水）。
3.  根据选择，询问对应单件物品的价格（如一个蛋糕的价格、一个披萨的价格、一瓶2升汽水的价格）。
4.  程序需要计算：
    *   需要购买多少件物品（例如，5个人，每人吃1/4个蛋糕，则需要 `ceil(5 * 0.25)` = 2个蛋糕）。
    *   这些物品的总成本。
5.  将结果输出给用户。

![](img/9e7f2d9c3bb1b18eedf189643cc1c69c_83.png)

![](img/9e7f2d9c3bb1b18eedf189643cc1c69c_85.png)

![](img/9e7f2d9c3bb1b18eedf189643cc1c69c_87.png)

**项目提交**：
*   你需要使用GitHub Classroom创建项目仓库。
*   在 `README.md` 文件中添加程序运行的截图。
*   根据提供的评分标准进行自我评估。

![](img/9e7f2d9c3bb1b18eedf189643cc1c69c_89.png)

---

## 总结

本节课我们一起学习了C++中实现决策的核心工具——分支结构。
*   我们掌握了如何使用 **`if`、`else if` 和 `else`** 语句来根据条件执行不同的代码路径。
*   我们了解了 **`switch`** 语句，它适用于基于单个表达式与多个常量值匹配的场景，并注意了 `break` 关键字的作用。
*   我们学习了构建条件的基石：**布尔表达式**、**关系运算符**（`>`, `<`, `==` 等）和**逻辑运算符**（`&&`, `||`, `!`）。
*   我们讨论了**运算符优先级**的重要性，并强调使用括号来确保复杂表达式的正确求值。

![](img/9e7f2d9c3bb1b18eedf189643cc1c69c_91.png)

掌握这些概念后，你的程序将不再只是简单地顺序执行，而是能够根据输入做出智能反应。接下来，请运用这些知识开始你的第一个项目——派对规划程序。