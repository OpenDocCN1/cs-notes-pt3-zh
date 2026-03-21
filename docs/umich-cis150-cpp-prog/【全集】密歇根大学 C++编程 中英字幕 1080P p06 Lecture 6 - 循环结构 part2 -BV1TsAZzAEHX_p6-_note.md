# C++编程：第6讲：循环结构（第二部分）

![](img/8a6c773aaca9051b333cb31051acb3c1_0.png)

![](img/8a6c773aaca9051b333cb31051acb3c1_2.png)

在本节课中，我们将继续深入学习C++中的循环结构。我们将探讨`break`和`continue`关键字、变量的作用域、枚举类型，并通过一个掷骰子的统计示例来巩固循环的应用。

![](img/8a6c773aaca9051b333cb31051acb3c1_4.png)

![](img/8a6c773aaca9051b333cb31051acb3c1_6.png)

---

![](img/8a6c773aaca9051b333cb31051acb3c1_8.png)

## 循环控制：`break`与`continue`

![](img/8a6c773aaca9051b333cb31051acb3c1_10.png)

上一节我们介绍了`for`循环和`while`循环的基本用法。本节中，我们来看看两个可以改变循环流程的关键字：`break`和`continue`。

![](img/8a6c773aaca9051b333cb31051acb3c1_12.png)

![](img/8a6c773aaca9051b333cb31051acb3c1_14.png)

![](img/8a6c773aaca9051b333cb31051acb3c1_15.png)

`break`关键字用于立即终止整个循环。无论循环条件是否满足，一旦执行到`break`，循环就会停止。

![](img/8a6c773aaca9051b333cb31051acb3c1_17.png)

```cpp
while (true) {
    // 这是一个无限循环
    if (number == INT_MAX) {
        break; // 当number达到最大值时，跳出循环
    }
    number++;
}
```

![](img/8a6c773aaca9051b333cb31051acb3c1_19.png)

![](img/8a6c773aaca9051b333cb31051acb3c1_21.png)

`continue`关键字用于跳过当前循环迭代中剩余的代码，直接开始下一次迭代。

```cpp
for (int i = 0; i < 100; i++) {
    if (i % 2 == 0) {
        continue; // 如果i是偶数，跳过本次循环的剩余部分
    }
    cout << i << endl; // 只打印奇数
}
```

![](img/8a6c773aaca9051b333cb31051acb3c1_23.png)

![](img/8a6c773aaca9051b333cb31051acb3c1_25.png)

虽然`break`和`continue`提供了便利，但它们有时会使代码逻辑变得不那么直观。通常，我们可以通过调整循环条件或使用`if-else`语句来达到相同的目的。

![](img/8a6c773aaca9051b333cb31051acb3c1_27.png)

![](img/8a6c773aaca9051b333cb31051acb3c1_29.png)

---

![](img/8a6c773aaca9051b333cb31051acb3c1_31.png)

## 变量的作用域

![](img/8a6c773aaca9051b333cb31051acb3c1_33.png)

变量的作用域决定了它在程序中的哪些部分可以被访问。一个基本原则是：变量在其被声明的代码块（由花括号`{}`界定）内有效。

以下是关于作用域的几个要点：
*   在循环内部声明的变量（例如`for`循环中的计数器`i`），其作用域仅限于该循环内部。循环结束后，该变量将无法被访问。
*   如果需要在循环结束后仍然使用某个变量的值，必须在循环外部声明该变量。
*   应避免在不同的作用域内使用相同的变量名，这可能导致混淆和错误。

![](img/8a6c773aaca9051b333cb31051acb3c1_35.png)

![](img/8a6c773aaca9051b333cb31051acb3c1_37.png)

![](img/8a6c773aaca9051b333cb31051acb3c1_39.png)

![](img/8a6c773aaca9051b333cb31051acb3c1_41.png)

```cpp
int number; // 在循环外部声明，作用域更广
for (int i = 0; i < 100; i++) { // i的作用域仅限于这个for循环
    number = i * 2;
}
// 这里可以访问number，但不能访问i
cout << number << endl;
```

![](img/8a6c773aaca9051b333cb31051acb3c1_43.png)

调试器是理解作用域和跟踪变量值的绝佳工具。

![](img/8a6c773aaca9051b333cb31051acb3c1_45.png)

---

![](img/8a6c773aaca9051b333cb31051acb3c1_47.png)

![](img/8a6c773aaca9051b333cb31051acb3c1_48.png)

## 枚举类型

![](img/8a6c773aaca9051b333cb31051acb3c1_50.png)

![](img/8a6c773aaca9051b333cb31051acb3c1_52.png)

枚举（`enum`）是一种用户定义的数据类型，它允许我们为整数值分配有意义的名称，从而使代码更易读、更安全。

定义一个枚举类型：
```cpp
enum LightState { LS_RED, LS_GREEN, LS_YELLOW, LS_DONE };
```

使用枚举类型：
```cpp
LightState currentLight = LS_RED;
while (currentLight == LS_RED) {
    cout << "Waiting at the red light." << endl;
    // ... 模拟等待 ...
    currentLight = LS_GREEN; // 切换状态
}
cout << "Green means go!" << endl;
```

![](img/8a6c773aaca9051b333cb31051acb3c1_54.png)

使用枚举的好处在于，编译器会确保变量只能被赋予枚举中定义的值，这比直接使用整数常量（如`0`代表红色）更加安全可靠。

![](img/8a6c773aaca9051b333cb31051acb3c1_56.png)

---

![](img/8a6c773aaca9051b333cb31051acb3c1_58.png)

![](img/8a6c773aaca9051b333cb31051acb3c1_59.png)

## 实践示例：掷骰子统计

现在，让我们运用循环来模拟掷骰子，并统计各点数出现的次数。这个例子展示了如何通过大量重复实验来观察随机事件的分布。

程序的核心步骤如下：
1.  询问用户想要模拟掷骰子的次数。
2.  初始化六个计数器，分别对应点数1到6。
3.  使用循环执行指定次数的“掷骰子”操作。每次使用随机数生成器模拟掷出一个1到6的点数。
4.  根据生成的随机数，增加对应点数的计数器。
5.  循环结束后，输出每个点数出现的次数。

```cpp
#include <iostream>
#include <cstdlib>
#include <ctime>
using namespace std;

![](img/8a6c773aaca9051b333cb31051acb3c1_61.png)

![](img/8a6c773aaca9051b333cb31051acb3c1_63.png)

![](img/8a6c773aaca9051b333cb31051acb3c1_65.png)

int main() {
    srand(time(0)); // 设置随机数种子

    int count1 = 0, count2 = 0, count3 = 0, count4 = 0, count5 = 0, count6 = 0;
    int numRolls;

    cout << "How many times do you want to roll? ";
    cin >> numRolls;

    for (int roll = 0; roll < numRolls; roll++) {
        int rollValue = (rand() % 6) + 1; // 生成1-6的随机数

        if (rollValue == 1) count1++;
        else if (rollValue == 2) count2++;
        else if (rollValue == 3) count3++;
        else if (rollValue == 4) count4++;
        else if (rollValue == 5) count5++;
        else count6++; // 一定是6
    }

    cout << "Count of 1s: " << count1 << endl;
    cout << "Count of 2s: " << count2 << endl;
    cout << "Count of 3s: " << count3 << endl;
    cout << "Count of 4s: " << count4 << endl;
    cout << "Count of 5s: " << count5 << endl;
    cout << "Count of 6s: " << count6 << endl;

    return 0;
}
```

![](img/8a6c773aaca9051b333cb31051acb3c1_67.png)

![](img/8a6c773aaca9051b333cb31051acb3c1_69.png)

随着掷骰子次数的增加（例如从10次增加到10万次），各个点数出现的次数会越来越接近，这验证了随机事件的均匀分布特性。目前，我们使用了多个独立的变量来存储计数，在后续学习了数组之后，我们可以用更简洁高效的方式重写这个程序。

![](img/8a6c773aaca9051b333cb31051acb3c1_71.png)

![](img/8a6c773aaca9051b333cb31051acb3c1_73.png)

![](img/8a6c773aaca9051b333cb31051acb3c1_75.png)

---

![](img/8a6c773aaca9051b333cb31051acb3c1_77.png)

![](img/8a6c773aaca9051b333cb31051acb3c1_79.png)

本节课中我们一起学习了循环控制语句`break`和`continue`，理解了变量作用域的重要性，认识了能使代码更清晰的枚举类型，并通过一个有趣的统计实例巩固了循环的运用。循环是编程中实现重复操作的基础工具，掌握它们对后续的学习至关重要。