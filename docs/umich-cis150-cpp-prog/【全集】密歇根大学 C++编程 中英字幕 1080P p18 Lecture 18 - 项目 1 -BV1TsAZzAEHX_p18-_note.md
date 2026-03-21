# C++编程：项目0：派对策划程序 🎉

![](img/04785d3c771cf9f526d2a80f5095a48f_0.png)

![](img/04785d3c771cf9f526d2a80f5095a48f_2.png)

![](img/04785d3c771cf9f526d2a80f5095a48f_4.png)

![](img/04785d3c771cf9f526d2a80f5095a48f_6.png)

![](img/04785d3c771cf9f526d2a80f5095a48f_8.png)

在本节课中，我们将回顾项目0的解决方案，并学习如何构建一个简单的派对策划程序。我们将涵盖用户输入、条件判断、循环验证以及基本的数学计算。

![](img/04785d3c771cf9f526d2a80f5095a48f_10.png)

![](img/04785d3c771cf9f526d2a80f5095a48f_12.png)

---

![](img/04785d3c771cf9f526d2a80f5095a48f_14.png)

![](img/04785d3c771cf9f526d2a80f5095a48f_16.png)

## 项目概述

项目0的目标是创建一个程序，帮助用户计算派对所需物品的数量和总成本。程序需要询问来宾人数、服务类型（蛋糕、披萨或汽水），并根据人均消耗量计算需要购买多少份完整物品，同时将结果向上取整。

## 核心步骤解析

![](img/04785d3c771cf9f526d2a80f5095a48f_18.png)

### 1. 询问来宾人数

![](img/04785d3c771cf9f526d2a80f5095a48f_20.png)

![](img/04785d3c771cf9f526d2a80f5095a48f_22.png)

![](img/04785d3c771cf9f526d2a80f5095a48f_23.png)

首先，程序需要询问有多少位客人会来参加派对。

![](img/04785d3c771cf9f526d2a80f5095a48f_25.png)

![](img/04785d3c771cf9f526d2a80f5095a48f_27.png)

```cpp
int numberOfGuests;
cout << "How many guests are coming to the party? ";
cin >> numberOfGuests;
// 记得加上主人自己
int totalPeople = numberOfGuests + 1;
```

### 2. 选择服务类型并验证

![](img/04785d3c771cf9f526d2a80f5095a48f_29.png)

接下来，询问用户将提供什么食物或饮料。为了确保输入有效，我们使用一个验证循环。

![](img/04785d3c771cf9f526d2a80f5095a48f_31.png)

![](img/04785d3c771cf9f526d2a80f5095a48f_33.png)

```cpp
string choice;
cout << "Are you serving cake, pizza, or pop? ";
cin >> choice;

![](img/04785d3c771cf9f526d2a80f5095a48f_35.png)

// 验证循环：确保输入是“cake”、“pizza”或“pop”之一
while (choice != "cake" && choice != "pizza" && choice != "pop") {
    cout << "Invalid choice. Please enter cake, pizza, or pop: ";
    cin >> choice;
}
```

![](img/04785d3c771cf9f526d2a80f5095a48f_37.png)

![](img/04785d3c771cf9f526d2a80f5095a48f_38.png)

![](img/04785d3c771cf9f526d2a80f5095a48f_40.png)

### 3. 确定人均消耗量

![](img/04785d3c771cf9f526d2a80f5095a48f_42.png)

根据用户的选择，设定每个人消耗的完整物品比例。

```cpp
double amountPerPerson = 0.0;
if (choice == "cake") {
    amountPerPerson = 0.25; // 每人消耗1/4个蛋糕
} else if (choice == "pizza") {
    amountPerPerson = 0.33333; // 每人消耗1/3个披萨
} else { // 只能是 pop
    amountPerPerson = 0.375; // 每人消耗3/8瓶汽水 (0.75升 / 2升)
}
```

### 4. 询问单价并计算所需数量

![](img/04785d3c771cf9f526d2a80f5095a48f_44.png)

询问单个物品的价格，并计算需要购买的总数量。注意，我们需要使用 `ceil` 函数将结果向上取整，因为不能购买部分物品。

![](img/04785d3c771cf9f526d2a80f5095a48f_46.png)

![](img/04785d3c771cf9f526d2a80f5095a48f_48.png)

![](img/04785d3c771cf9f526d2a80f5095a48f_50.png)

```cpp
double pricePerItem;
cout << "How much does it cost to buy one " << choice << "? ";
cin >> pricePerItem;

![](img/04785d3c771cf9f526d2a80f5095a48f_52.png)

![](img/04785d3c771cf9f526d2a80f5095a48f_54.png)

// 计算所需物品数量并向上取整
double itemsNeeded = totalPeople * amountPerPerson;
itemsNeeded = ceil(itemsNeeded); // 使用ceil函数向上取整
// 引用来源：cplusplus.com/reference/cmath/ceil/
```

![](img/04785d3c771cf9f526d2a80f5095a48f_56.png)

![](img/04785d3c771cf9f526d2a80f5095a48f_57.png)

### 5. 输出结果

![](img/04785d3c771cf9f526d2a80f5095a48f_59.png)

最后，向用户展示需要购买多少物品以及总成本。

```cpp
cout << "To serve " << totalPeople << " people " << choice
     << " at your party, you need to buy " << itemsNeeded
     << " " << choice << "(s)." << endl;
cout << "Your party will cost about $" << (pricePerItem * itemsNeeded) << "." << endl;
```

---

## 测试程序

为了确保程序正确运行，我们需要进行测试。以下是一些测试用例：

1.  **蛋糕**：4位客人，蛋糕单价$2。总人数为5，需要 `ceil(5 * 0.25) = ceil(1.25) = 2` 个蛋糕。总成本应为 $4。
2.  **披萨**：3位客人，披萨单价$6.75。总人数为4，需要 `ceil(4 * 1/3) = ceil(1.333...) = 2` 个披萨。总成本应为 $13.50。
3.  **汽水**：2位客人，汽水单价$2.99。总人数为3，需要 `ceil(3 * 3/8) = ceil(1.125) = 2` 瓶汽水。总成本应为 $5.98。

运行程序并验证输出是否符合这些预期结果。

---

## 项目总结

在本节课中，我们一起学习了如何构建项目0的派对策划程序。我们实践了以下核心概念：
*   使用 `cin` 和 `cout` 进行基本的输入输出。
*   使用 `if-else` 语句进行条件判断。
*   使用 `while` 循环进行输入验证。
*   使用 `ceil()` 函数进行数学上的向上取整。
*   将问题分解为清晰的步骤并组合成完整的程序。

![](img/04785d3c771cf9f526d2a80f5095a48f_61.png)

这个项目是后续更复杂编程任务的良好开端。请确保在提交前运行你的程序，并按照要求完成自评。