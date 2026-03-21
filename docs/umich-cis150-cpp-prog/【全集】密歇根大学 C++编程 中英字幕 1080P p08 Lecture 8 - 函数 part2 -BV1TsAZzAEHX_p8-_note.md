# C++编程：第8讲：函数（第二部分）🎯

![](img/57c268b08bd56c88e936f4888a44dcda_0.png)

在本节课中，我们将继续深入学习C++函数，探讨一些高级特性，如默认参数、函数重载、作用域以及如何将函数组织到独立的文件中。这些知识将帮助你编写更灵活、更易维护的代码。

---

## 函数的作用与重要性

上一节我们介绍了函数的基础概念。本节中，我们来看看函数更深层次的价值。

函数不仅能减少代码重复，更重要的是为代码块赋予有意义的名称，这极大地提升了代码的可读性和可维护性。软件的生命周期很长，清晰的代码结构对于长期的维护和更新至关重要。

## 变量的作用域

![](img/57c268b08bd56c88e936f4888a44dcda_2.png)

![](img/57c268b08bd56c88e936f4888a44dcda_4.png)

![](img/57c268b08bd56c88e936f4888a44dcda_5.png)

在深入新特性之前，我们需要理解变量的作用域。变量的作用域决定了它在代码中的可见性和生命周期。

*   **局部变量**：在函数或代码块（如循环）内部声明的变量。它们只在该函数或代码块内有效。
*   **全局变量**：在所有函数之外声明的变量。理论上，程序中的任何函数都可以访问和修改它。

![](img/57c268b08bd56c88e936f4888a44dcda_7.png)

**示例：局部变量与全局变量**
```cpp
int globalNumber = 10; // 全局变量

![](img/57c268b08bd56c88e936f4888a44dcda_8.png)

![](img/57c268b08bd56c88e936f4888a44dcda_9.png)

![](img/57c268b08bd56c88e936f4888a44dcda_11.png)

void addToNumber() {
    int localNumber = 5; // 局部变量，仅在此函数内有效
    globalNumber += localNumber; // 可以访问和修改全局变量
}

int main() {
    addToNumber();
    cout << globalNumber; // 输出 15
    // cout << localNumber; // 错误！localNumber 在此处不可见
    return 0;
}
```

![](img/57c268b08bd56c88e936f4888a44dcda_13.png)

![](img/57c268b08bd56c88e936f4888a44dcda_15.png)

**注意**：虽然可以使用全局变量，但过度使用会导致代码难以理解和维护。通常，更好的做法是通过参数传递和返回值在函数间交换数据。

## 默认参数值

![](img/57c268b08bd56c88e936f4888a44dcda_17.png)

![](img/57c268b08bd56c88e936f4888a44dcda_19.png)

有时，我们希望函数的某些参数在调用者不提供时，能自动使用一个预设值。这可以通过**默认参数**来实现。

![](img/57c268b08bd56c88e936f4888a44dcda_21.png)

![](img/57c268b08bd56c88e936f4888a44dcda_23.png)

默认参数必须在参数列表的**末尾**依次定义。因为C++是根据参数的位置来匹配的。

![](img/57c268b08bd56c88e936f4888a44dcda_25.png)

![](img/57c268b08bd56c88e936f4888a44dcda_27.png)

**示例：带默认参数的函数**
```cpp
// 假设下限默认为1，上限必须提供
int getInputWithinRange(int upperBound, int lowerBound = 1) {
    int userInput;
    // ... 验证输入是否在 [lowerBound, upperBound] 范围内的逻辑 ...
    return userInput;
}

![](img/57c268b08bd56c88e936f4888a44dcda_29.png)

![](img/57c268b08bd56c88e936f4888a44dcda_31.png)

int main() {
    int num1 = getInputWithinRange(10); // 相当于 getInputWithinRange(10, 1)
    int num2 = getInputWithinRange(100, 50); // 提供下限50
    return 0;
}
```

## 函数重载

C++允许我们定义多个**同名函数**，只要它们的**参数列表（参数的类型、数量或顺序）不同**。这被称为**函数重载**。编译器会根据调用时提供的实参来决定使用哪个版本。

![](img/57c268b08bd56c88e936f4888a44dcda_33.png)

![](img/57c268b08bd56c88e936f4888a44dcda_35.png)

**示例：函数重载**
```cpp
// 版本1：接受整数参数
string getDate(int day, int month = 10, int year = 2025) {
    return to_string(year) + "-" + to_string(month) + "-" + to_string(day);
}

![](img/57c268b08bd56c88e936f4888a44dcda_37.png)

![](img/57c268b08bd56c88e936f4888a44dcda_38.png)

![](img/57c268b08bd56c88e936f4888a44dcda_40.png)

![](img/57c268b08bd56c88e936f4888a44dcda_42.png)

// 版本2：接受字符串参数（参数类型不同，构成重载）
string getDate(string day, string month = "10", string year = "2025") {
    return year + "-" + month + "-" + day;
}

![](img/57c268b08bd56c88e936f4888a44dcda_44.png)

![](img/57c268b08bd56c88e936f4888a44dcda_46.png)

![](img/57c268b08bd56c88e936f4888a44dcda_48.png)

int main() {
    cout << getDate(15); // 调用版本1，输出 "2025-10-15"
    cout << getDate("15", "12"); // 调用版本2，输出 "2025-12-15"
    return 0;
}
```

![](img/57c268b08bd56c88e936f4888a44dcda_50.png)

![](img/57c268b08bd56c88e936f4888a44dcda_52.png)

![](img/57c268b08bd56c88e936f4888a44dcda_54.png)

![](img/57c268b08bd56c88e936f4888a44dcda_56.png)

![](img/57c268b08bd56c88e936f4888a44dcda_58.png)

**重要**：仅靠**返回值类型不同**不足以构成函数重载，因为编译器无法仅通过返回值确定调用哪个函数。

## 参数验证

![](img/57c268b08bd56c88e936f4888a44dcda_60.png)

在函数内部对传入的参数进行验证是一个好习惯。这可以确保后续的计算或操作基于有效的数据。

![](img/57c268b08bd56c88e936f4888a44dcda_62.png)

![](img/57c268b08bd56c88e936f4888a44dcda_64.png)

![](img/57c268b08bd56c88e936f4888a44dcda_66.png)

**示例：简单的日期验证**
```cpp
bool isValidDate(int day, int month, int year) {
    if (month < 1 || month > 12) return false;
    if (day < 1) return false;

    // 检查每月天数（简化版，未考虑闰年）
    int daysInMonth;
    if (month == 2) {
        daysInMonth = 28;
    } else if (month == 4 || month == 6 || month == 9 || month == 11) {
        daysInMonth = 30;
    } else {
        daysInMonth = 31;
    }

    if (day > daysInMonth) return false;
    // 可以添加年份验证（如范围）
    return true;
}
```

## 分离代码文件：头文件(.h)

![](img/57c268b08bd56c88e936f4888a44dcda_68.png)

![](img/57c268b08bd56c88e936f4888a44dcda_70.png)

当项目变大时，将函数声明和定义分离到不同的文件中是一种良好的组织方式。通常，我们将函数声明放在**头文件**（.h 或 .hpp）中，将函数定义放在**源文件**（.cpp）中。

![](img/57c268b08bd56c88e936f4888a44dcda_72.png)

![](img/57c268b08bd56c88e936f4888a44dcda_74.png)

![](img/57c268b08bd56c88e936f4888a44dcda_75.png)

![](img/57c268b08bd56c88e936f4888a44dcda_77.png)

1.  **创建头文件** (例如 `myFunctions.h`)：
    ```cpp
    // myFunctions.h
    #pragma once // 防止头文件被重复包含（Visual Studio）
    // 或者使用传统的防护宏：
    // #ifndef MY_FUNCTIONS_H
    // #define MY_FUNCTIONS_H

    #include <string>
    using namespace std;

    // 函数声明
    string getDate(int day, int month = 10, int year = 2025);
    bool isValidDate(int day, int month, int year);

    // #endif // MY_FUNCTIONS_H
    ```

![](img/57c268b08bd56c88e936f4888a44dcda_79.png)

![](img/57c268b08bd56c88e936f4888a44dcda_81.png)

2.  **创建对应的源文件** (例如 `myFunctions.cpp`)：
    ```cpp
    // myFunctions.cpp
    #include "myFunctions.h"
    #include <iostream>
    using namespace std;

    // 函数定义
    string getDate(int day, int month, int year) {
        // ... 实现代码 ...
    }

    bool isValidDate(int day, int month, int year) {
        // ... 实现代码 ...
    }
    ```

3.  **在主程序中使用**：
    ```cpp
    // main.cpp
    #include <iostream>
    #include "myFunctions.h" // 包含自定义头文件

    int main() {
        if (isValidDate(31, 12, 2024)) {
            cout << getDate(31, 12, 2024);
        }
        return 0;
    }
    ```

![](img/57c268b08bd56c88e936f4888a44dcda_83.png)

![](img/57c268b08bd56c88e936f4888a44dcda_84.png)

这样做的好处是代码结构清晰，易于管理，并且在大型项目中能显著提高编译效率。

![](img/57c268b08bd56c88e936f4888a44dcda_86.png)

---

![](img/57c268b08bd56c88e936f4888a44dcda_88.png)

![](img/57c268b08bd56c88e936f4888a44dcda_90.png)

本节课中我们一起学习了C++函数的进阶主题。我们探讨了变量作用域的概念，学会了如何使用默认参数让函数调用更简洁，了解了通过函数重载使一个函数名能应对多种情况，并强调了参数验证的重要性。最后，我们介绍了如何通过头文件(.h)和源文件(.cpp)来组织代码，这是构建大型、可维护C++项目的基础。掌握这些概念，将使你的编程能力更上一层楼。