# C++编程：17：面向对象编程 part2

![](img/2354747665c9aab38f92ad4c45f244f5_0.png)

![](img/2354747665c9aab38f92ad4c45f244f5_0.png)

在本节课中，我们将要学习面向对象编程的剩余部分，包括如何将类分离到不同的文件中、如何进行单元测试、函数重载、运算符重载以及静态成员。最后，我们还将初步介绍指针的概念。

![](img/2354747665c9aab38f92ad4c45f244f5_2.png)

## 分离文件与单元测试

![](img/2354747665c9aab38f92ad4c45f244f5_4.png)

上一节我们介绍了类和对象的基本概念。本节中我们来看看如何将代码组织得更好，并确保其正确性。

将不同类的代码放在同一个文件中会显得混乱。更好的做法是将每个类放在独立的文件中。在C++中，通常使用头文件（.h）来声明类，使用源文件（.cpp）来实现类。为了简化，我们可以将所有内容都放在头文件中。

![](img/2354747665c9aab38f92ad4c45f244f5_6.png)

以下是如何创建一个头文件：

![](img/2354747665c9aab38f92ad4c45f244f5_8.png)

```cpp
// lotto_ticket.h
#pragma once
#include <vector>
using namespace std;

![](img/2354747665c9aab38f92ad4c45f244f5_10.png)

class LottoTicket {
private:
    int number1;
    int number2;
    int number3;
public:
    LottoTicket(int n1, int n2, int n3);
    LottoTicket(vector<int> numbers);
    bool isWinner(const LottoTicket& winningTicket) const;
};
```

![](img/2354747665c9aab38f92ad4c45f244f5_12.png)

创建头文件后，在主程序中需要包含它：

```cpp
#include "lotto_ticket.h"
```

仅仅编写代码还不够，我们需要验证代码是否按预期工作。手动检查输出容易出错。更好的方法是编写代码来自动测试我们的代码，这就是单元测试。

以下是设置单元测试的步骤：

1.  在解决方案中添加一个新的“本机单元测试项目”。
2.  在测试项目中，包含需要测试的类的头文件。由于文件在不同目录，可能需要指定路径，例如 `#include "../Week11_Classes/lotto_ticket.h"`。
3.  编写测试方法。一个常见的模式是AAA模式：准备（Arrange）、执行（Act）、断言（Assert）。

以下是一个测试示例：

```cpp
TEST_METHOD(WinningTicketTest)
{
    // Arrange: 设置测试所需变量
    LottoTicket ticket(1, 2, 3);
    LottoTicket winningTicket(1, 2, 3);

    // Act: 调用被测试的代码
    bool result = ticket.isWinner(winningTicket);

    // Assert: 验证结果是否符合预期
    Assert::IsTrue(result);
}
```

编写测试后，可以通过“测试资源管理器”运行所有测试。通过的测试会显示绿色对勾，失败的则显示红色叉号。单元测试有助于在修改代码后快速确认原有功能未被破坏，是软件开发中的重要实践，常与持续集成和持续部署结合使用。

## 函数与运算符重载

![](img/2354747665c9aab38f92ad4c45f244f5_14.png)

![](img/2354747665c9aab38f92ad4c45f244f5_15.png)

![](img/2354747665c9aab38f92ad4c45f244f5_16.png)

在C++中，我们可以为同一个函数名定义多个版本，只要它们的参数列表不同，这称为函数重载。构造函数也可以重载。

例如，`LottoTicket`类可以有两个构造函数：

```cpp
LottoTicket(int n1, int n2, int n3);
LottoTicket(vector<int> numbers);
```

![](img/2354747665c9aab38f92ad4c45f244f5_18.png)

这样，创建对象时既可以直接传入三个整数，也可以传入一个整数向量。

![](img/2354747665c9aab38f92ad4c45f244f5_20.png)

![](img/2354747665c9aab38f92ad4c45f244f5_22.png)

运算符重载允许我们为自定义类型（类）定义运算符的行为，例如 `+`, `-`, `==` 等。这需要为运算符定义特殊的成员函数。

![](img/2354747665c9aab38f92ad4c45f244f5_24.png)

![](img/2354747665c9aab38f92ad4c45f244f5_26.png)

![](img/2354747665c9aab38f92ad4c45f244f5_28.png)

![](img/2354747665c9aab38f92ad4c45f244f5_29.png)

以下是可重载的运算符列表：
*   算术运算符：`+`, `-`, `*`, `/`, `%`
*   关系运算符：`==`, `!=`, `<`, `>`, `<=`, `>=`
*   赋值运算符：`=`
*   下标运算符：`[]`
*   函数调用运算符：`()`

## 静态成员

![](img/2354747665c9aab38f92ad4c45f244f5_31.png)

到目前为止，类的每个对象都拥有自己的一套数据成员副本，这些称为实例成员。有时，我们希望所有对象共享同一个数据成员，这时可以使用静态成员。

![](img/2354747665c9aab38f92ad4c45f244f5_33.png)

静态成员属于类本身，而不是类的某个特定对象。它在内存中只存在一份，被所有对象共享。静态成员变量需要在类外进行定义和初始化。

例如，可以为`LottoTicket`类添加一个静态常量来表示彩票价格：

```cpp
// 在类定义中声明
class LottoTicket {
public:
    static const double TICKET_PRICE;
    // ... 其他成员
};

// 在类外定义和初始化
const double LottoTicket::TICKET_PRICE = 1.0;
```

![](img/2354747665c9aab38f92ad4c45f244f5_35.png)

静态成员函数则不能访问类的非静态成员，因为它没有`this`指针。

![](img/2354747665c9aab38f92ad4c45f244f5_37.png)

![](img/2354747665c9aab38f92ad4c45f244f5_38.png)

![](img/2354747665c9aab38f92ad4c45f244f5_40.png)

## 指针初步

![](img/2354747665c9aab38f92ad4c45f244f5_42.png)

![](img/2354747665c9aab38f92ad4c45f244f5_43.png)

![](img/2354747665c9aab38f92ad4c45f244f5_45.png)

指针是C++中一个强大但容易出错的概念。指针是一个变量，其存储的值是另一个变量的内存地址。

![](img/2354747665c9aab38f92ad4c45f244f5_47.png)

![](img/2354747665c9aab38f92ad4c45f244f5_49.png)

要声明一个指针，在类型后使用`*`符号：

```cpp
int* numberPtr; // 声明一个指向整数的指针
```

`&`运算符用于获取变量的地址：

```cpp
int number = 42;
numberPtr = &number; // numberPtr 指向 number 的内存地址
```

`*`运算符用于解引用指针，即访问指针所指向地址中存储的值：

```cpp
*numberPtr = 77; // 将 number 的值改为 77
cout << *numberPtr; // 输出 77
cout << numberPtr; // 输出 number 的内存地址（如0x7fff5fbff8ac）
```

指针的一个常见用途是动态内存分配。这允许我们在程序运行时请求内存，例如创建大小在运行时才确定的数组。

使用`new`运算符在堆上分配内存：

![](img/2354747665c9aab38f92ad4c45f244f5_51.png)

```cpp
int size;
cin >> size;
int* dynamicArray = new int[size]; // 动态分配一个大小为 size 的整数数组

for (int i = 0; i < size; ++i) {
    cin >> dynamicArray[i]; // 像普通数组一样使用
}

// 使用完毕后，必须用 delete[] 释放内存，防止内存泄漏
delete[] dynamicArray;
```

![](img/2354747665c9aab38f92ad4c45f244f5_53.png)

![](img/2354747665c9aab38f92ad4c45f244f5_55.png)

![](img/2354747665c9aab38f92ad4c45f244f5_57.png)

![](img/2354747665c9aab38f92ad4c45f244f5_58.png)

![](img/2354747665c9aab38f92ad4c45f244f5_60.png)

忘记释放动态分配的内存会导致内存泄漏，即程序持续占用不再使用的内存。

![](img/2354747665c9aab38f92ad4c45f244f5_62.png)

![](img/2354747665c9aab38f92ad4c45f244f5_64.png)

## 最终项目介绍

本节课的最后，我们介绍了本课程的最终项目：开发一个简化版的“大富翁”游戏。

项目基本要求如下：
*   创建一个10x10的棋盘（共40个格子）。
*   支持2到8名玩家，初始资金为$1500。
*   玩家掷两个六面骰子前进。
*   包含“起点”、“监狱”等特殊格子（功能可简化）。
*   玩家可以购买地产，当其他玩家踏上时需支付租金。
*   程序需支持开始新游戏和加载保存的游戏。
*   必须使用类来组织代码（如`Player`, `Property`类）。

![](img/2354747665c9aab38f92ad4c45f244f5_66.png)

![](img/2354747665c9aab38f92ad4c45f244f5_68.png)

项目提交要求：
*   将代码托管在GitHub仓库。
*   至少需要有10次有效提交，分布在10个不同的日期，每次提交都应包含可运行代码的截图。
*   可以选择与一名伙伴合作完成。

![](img/2354747665c9aab38f92ad4c45f244f5_70.png)

在课程最后，需要进行项目演示，展示游戏的基本功能，并能解释代码的关键部分。

![](img/2354747665c9aab38f92ad4c45f244f5_72.png)

![](img/2354747665c9aab38f92ad4c45f244f5_73.png)

![](img/2354747665c9aab38f92ad4c45f244f5_74.png)

![](img/2354747665c9aab38f92ad4c45f244f5_75.png)

## 总结

![](img/2354747665c9aab38f92ad4c45f244f5_77.png)

![](img/2354747665c9aab38f92ad4c45f244f5_79.png)

![](img/2354747665c9aab38f92ad4c45f244f5_81.png)

本节课中我们一起学习了面向对象编程的更多高级主题。我们了解了如何通过分离文件来更好地组织代码结构，并掌握了编写单元测试来自动验证代码正确性的方法。我们还探讨了函数重载和运算符重载，它们能增加代码的灵活性。静态成员让我们可以在类的所有实例间共享数据。最后，我们初步接触了指针的概念，包括其声明、使用以及动态内存分配，这是后续深入学习C++的重要基础。通过这些知识，你将能够编写更结构化、更健壮且更易于维护的C++程序。