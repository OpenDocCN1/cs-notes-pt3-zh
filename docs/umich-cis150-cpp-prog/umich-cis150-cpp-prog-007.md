# 007：函数（第一部分）📚

![](img/7ba12b17bbb1cd80d74bc34847e1c74f_0.png)

![](img/7ba12b17bbb1cd80d74bc34847e1c74f_2.png)

![](img/7ba12b17bbb1cd80d74bc34847e1c74f_3.png)

在本节课中，我们将要学习C++中一个非常重要的概念：函数。函数本身并不能让我们做任何新的事情，但它能帮助我们编写更整洁、更高效的代码。一个很好的经验法则是：如果相同的代码出现了两次，我们就应该考虑使用函数来避免重复。本章内容将分为两周学习，作业提交截止日期是10月13日。

![](img/7ba12b17bbb1cd80d74bc34847e1c74f_5.png)

---

## 什么是函数？🤔

我们其实一直在使用函数。例如，`int main()` 本身就是一个函数。此外，像 `ceil(3.5)` 这样的数学函数也是函数。函数可以接收输入（参数），执行一些操作，并可能返回一个结果。

在C++中，我们通常将自定义的函数写在 `main` 函数的上方，以便于查找。一个函数的基本结构包括：
*   **返回类型**：函数返回值的类型（如 `int`, `double`, `void`）。
*   **函数名**：函数的标识符。
*   **参数列表**：函数接收的输入，放在括号 `()` 内。
*   **函数体**：函数要执行的代码，放在花括号 `{}` 内。
*   **`return` 语句**：用于返回结果（`void` 函数可以没有）。

下面是一个简单的函数示例，它总是返回整数10：

![](img/7ba12b17bbb1cd80d74bc34847e1c74f_7.png)

```cpp
int someNumber() {
    return 10;
}
```

![](img/7ba12b17bbb1cd80d74bc34847e1c74f_9.png)

我们可以在 `main` 函数中调用它：`cout << someNumber();`。

![](img/7ba12b17bbb1cd80d74bc34847e1c74f_11.png)

![](img/7ba12b17bbb1cd80d74bc34847e1c74f_13.png)

使用调试器的“步入”功能，可以进入函数内部观察其执行过程，理解代码是如何跳转和返回的。

---

## 创建更实用的函数⚙️

上一节我们介绍了一个简单的函数，本节中我们来看看如何创建更实用、可定制的函数。

![](img/7ba12b17bbb1cd80d74bc34847e1c74f_15.png)

![](img/7ba12b17bbb1cd80d74bc34847e1c74f_17.png)

### 生成随机数的函数

我们可以创建一个函数，让它返回一个指定范围内的随机数。这个函数需要接收一个参数，即随机数的最大值。

```cpp
int getRandomNumber(int maxNumber) {
    return (rand() % maxNumber) + 1;
}
```

![](img/7ba12b17bbb1cd80d74bc34847e1c74f_19.png)

![](img/7ba12b17bbb1cd80d74bc34847e1c74f_21.png)

调用方式：`getRandomNumber(100)` 会返回一个1到100之间的随机数。

![](img/7ba12b17bbb1cd80d74bc34847e1c74f_23.png)

### 不返回值的函数

有些函数只执行操作，不返回任何值。这时我们使用 `void` 作为返回类型。

例如，一个打印指定大小和字符的三角形的函数：

```cpp
void printTriangle(int size, char character) {
    for (int row = 1; row <= size; row++) {
        for (int col = 1; col <= row; col++) {
            cout << character;
        }
        cout << endl;
    }
}
```

调用方式：`printTriangle(10, '*');`。

函数的一个巨大优势是 **功能分解**。它允许我们将一个大问题分解成许多小问题，逐个解决。每个函数只负责一个明确的小任务，这使得代码更易于设计、理解和维护。

---

## 参数传递：传值与传引用🔗

![](img/7ba12b17bbb1cd80d74bc34847e1c74f_25.png)

在上一节创建的函数中，我们只是使用了参数的值。本节中我们来看看如何通过函数修改外部变量的值，这涉及到两种参数传递方式。

![](img/7ba12b17bbb1cd80d74bc34847e1c74f_27.png)

![](img/7ba12b17bbb1cd80d74bc34847e1c74f_29.png)

![](img/7ba12b17bbb1cd80d74bc34847e1c74f_31.png)

### 传值

![](img/7ba12b17bbb1cd80d74bc34847e1c74f_33.png)

默认情况下，C++是**传值**调用。这意味着函数内部得到的是参数值的一个副本。在函数内部修改这个参数，**不会影响**函数外部的原始变量。

![](img/7ba12b17bbb1cd80d74bc34847e1c74f_35.png)

```cpp
void tryToChange(int num) {
    num = num + 10; // 只修改了副本
}
int main() {
    int value = 5;
    tryToChange(value);
    cout << value; // 输出仍然是 5
}
```

### 传引用

![](img/7ba12b17bbb1cd80d74bc34847e1c74f_37.png)

![](img/7ba12b17bbb1cd80d74bc34847e1c74f_38.png)

如果我们希望函数能够修改外部变量的值，就需要使用**传引用**调用。在参数类型后加上 `&` 符号即可。

![](img/7ba12b17bbb1cd80d74bc34847e1c74f_40.png)

![](img/7ba12b17bbb1cd80d74bc34847e1c74f_42.png)

![](img/7ba12b17bbb1cd80d74bc34847e1c74f_44.png)

![](img/7ba12b17bbb1cd80d74bc34847e1c74f_46.png)

```cpp
void actuallyChange(int &num) { // 注意 & 符号
    num = num + 10; // 修改了原始变量
}
int main() {
    int value = 5;
    actuallyChange(value);
    cout << value; // 输出是 15
}
```

![](img/7ba12b17bbb1cd80d74bc34847e1c74f_48.png)

![](img/7ba12b17bbb1cd80d74bc34847e1c74f_49.png)

传引用在需要函数返回多个结果时非常有用，因为一个函数只能通过 `return` 返回一个值。例如，求解一元二次方程的两个根：

```cpp
string findIntercepts(double a, double b, double c, double &root1, double &root2) {
    double determinant = b * b - 4 * a * c;
    if (determinant < 0) {
        return "No intercepts found";
    }
    root1 = (-b + sqrt(determinant)) / (2 * a);
    root2 = (-b - sqrt(determinant)) / (2 * a);
    return "Intercepts found";
}
```

![](img/7ba12b17bbb1cd80d74bc34847e1c74f_51.png)

![](img/7ba12b17bbb1cd80d74bc34847e1c74f_53.png)

---

## 测试函数：断言（assert）🧪

我们常常会写错代码，自己却难以发现。让计算机自动检查代码的正确性是一个好习惯。C++标准库中的 `assert` 宏可以用于简单的单元测试。

以下是使用 `assert` 测试 `findIntercepts` 函数的示例：

```cpp
#include <cassert>
int main() {
    double r1, r2;
    findIntercepts(2, 3, -2, r1, r2);
    assert(r1 == 0.5);   // 检查第一个根是否为0.5
    assert(r2 == -2.0);  // 检查第二个根是否为-2.0
    cout << "All tests passed!" << endl;
}
```

如果断言失败（条件为假），程序会崩溃并报错。虽然 `assert` 在教学中比较简单，但在实际项目中，有更强大的测试框架（如Visual Studio的单元测试项目、Google Test等）可以集成到持续集成/持续部署流程中，实现自动化测试。

---

![](img/7ba12b17bbb1cd80d74bc34847e1c74f_55.png)

## 构建可重用的工具函数🧰

前面我们学习了函数的基本用法和测试。本节中我们来看看如何将常见的代码模式抽象成可重用的工具函数，这能极大减少代码重复。

![](img/7ba12b17bbb1cd80d74bc34847e1c74f_57.png)

### 获取范围内整数的函数

输入验证是我们经常需要写的代码。我们可以将其封装成一个函数：

```cpp
int getUserInputInRange(int lower, int upper) {
    int value;
    cout << "Enter a value between " << lower << " and " << upper << ": ";
    cin >> value;
    while (value < lower || value > upper) {
        cout << "Invalid, try again: ";
        cin >> value;
    }
    return value;
}
```

![](img/7ba12b17bbb1cd80d74bc34847e1c74f_59.png)

![](img/7ba12b17bbb1cd80d74bc34847e1c74f_61.png)

这样，无论何时需要获取某个范围内的整数，只需调用此函数即可，例如 `int size = getUserInputInRange(1, 100);`。

### 获取有效字符输入的函数

同样，我们可以编写一个函数来确保用户输入的是我们允许的字符之一：

```cpp
char getCharFromUser(string prompt, string validChars) {
    char input;
    bool isValid = false;
    while (!isValid) {
        cout << prompt;
        cin >> input;
        // 将输入转换为小写以便比较（可选）
        input = tolower(input);
        // 检查输入是否在有效字符列表中
        for (char c : validChars) {
            if (input == c) {
                isValid = true;
                break; // 找到匹配，跳出循环
            }
        }
    }
    return input;
}
```

调用方式：`char choice = getCharFromUser("Play again? (y/n): ", "yn");`。

---

![](img/7ba12b17bbb1cd80d74bc34847e1c74f_63.png)

## 常见错误与总结📝

![](img/7ba12b17bbb1cd80d74bc34847e1c74f_65.png)

在本节课中，我们一起学习了C++函数的基础知识。让我们回顾一下重点并看看常见的错误。

### 常见错误
以下是编写函数时需要注意的几个常见错误：
*   **忘记返回语句**：非 `void` 函数的所有执行路径都必须有 `return` 语句。
*   **参数类型不匹配**：调用函数时传递的参数类型必须与函数声明一致。
*   **忽略了传值与传引用的区别**：需要修改外部变量时，忘记使用 `&`。
*   **复制粘贴错误**：复制函数代码进行修改时，忘记更改函数名或返回的变量名。

### 总结

![](img/7ba12b17bbb1cd80d74bc34847e1c74f_67.png)

本节课我们主要学习了：
1.  **函数的目的**：组织代码、避免重复、实现功能分解，使程序更清晰、更易维护。
2.  **函数的定义与调用**：包括返回类型、函数名、参数列表和函数体。
3.  **参数传递**：理解了**传值**（操作副本）和**传引用**（操作原始变量，使用 `&`）的关键区别。
4.  **函数测试**：使用 `assert` 进行简单的自动化测试，并了解了工业级测试的基本概念。
5.  **构建实用函数**：将输入验证等常见模式抽象成可重用的工具函数。

![](img/7ba12b17bbb1cd80d74bc34847e1c74f_69.png)

函数是构建复杂程序的基石。通过将代码组织成一个个具有明确功能的函数，我们可以像搭积木一样构建出强大的软件。在接下来的项目和课程中，我们将大量使用函数。