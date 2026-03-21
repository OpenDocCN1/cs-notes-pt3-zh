# 012：流（第一部分）📂

![](img/2c41e5cacb23fe0abcd3d6b0bf88f28e_0.png)

在本节课中，我们将学习C++中的流（Streams），特别是如何从文件读取数据以及向文件写入数据。这将使我们的程序能够保存信息，并在程序的不同运行之间保持数据。

---

![](img/2c41e5cacb23fe0abcd3d6b0bf88f28e_2.png)

![](img/2c41e5cacb23fe0abcd3d6b0bf88f28e_4.png)

## 概述

![](img/2c41e5cacb23fe0abcd3d6b0bf88f28e_6.png)

![](img/2c41e5cacb23fe0abcd3d6b0bf88f28e_8.png)

到目前为止，我们的程序只在运行时处理信息，程序结束后信息就会丢失。通过使用流，我们可以从文件读取数据，也可以将数据写入文件，从而实现数据的持久化存储。本章节将介绍基本的文件输入输出操作。

## 流的基本概念

我们已经使用过流，例如 `cin` 和 `cout`，它们是标准的输入和输出流。要使用文件流，我们需要包含 `<fstream>` 库。

![](img/2c41e5cacb23fe0abcd3d6b0bf88f28e_10.png)

```cpp
#include <fstream>
```

![](img/2c41e5cacb23fe0abcd3d6b0bf88f28e_12.png)

![](img/2c41e5cacb23fe0abcd3d6b0bf88f28e_14.png)

![](img/2c41e5cacb23fe0abcd3d6b0bf88f28e_16.png)

## 输出格式化

在输出数据时，我们可以使用一些操作符来格式化输出，例如设置精度、宽度或填充字符。这些操作符属于 `<iomanip>` 库。

![](img/2c41e5cacb23fe0abcd3d6b0bf88f28e_18.png)

![](img/2c41e5cacb23fe0abcd3d6b0bf88f28e_20.png)

![](img/2c41e5cacb23fe0abcd3d6b0bf88f28e_22.png)

```cpp
#include <iomanip>
cout << setprecision(2) << fixed << 3.14159;
```

以下是常用的格式化操作符：

![](img/2c41e5cacb23fe0abcd3d6b0bf88f28e_24.png)

![](img/2c41e5cacb23fe0abcd3d6b0bf88f28e_25.png)

*   **`setprecision(n)`**: 设置浮点数输出的精度（位数）。
*   **`fixed`**: 使用定点表示法输出浮点数。
*   **`scientific`**: 使用科学计数法输出浮点数。
*   **`setw(n)`**: 设置下一个输出字段的最小宽度。
*   **`setfill(c)`**: 设置用于填充宽度的字符。

![](img/2c41e5cacb23fe0abcd3d6b0bf88f28e_27.png)

![](img/2c41e5cacb23fe0abcd3d6b0bf88f28e_28.png)

## 读取输入

![](img/2c41e5cacb23fe0abcd3d6b0bf88f28e_30.png)

![](img/2c41e5cacb23fe0abcd3d6b0bf88f28e_32.png)

![](img/2c41e5cacb23fe0abcd3d6b0bf88f28e_34.png)

从用户获取输入时，`cin` 会在遇到空格时停止读取。为了读取包含空格的整行文本，我们可以使用 `getline` 函数。

![](img/2c41e5cacb23fe0abcd3d6b0bf88f28e_36.png)

```cpp
string fullName;
cout << "Enter your full name: ";
getline(cin, fullName);
cout << "Your name is: " << fullName;
```

## 字符串流

![](img/2c41e5cacb23fe0abcd3d6b0bf88f28e_38.png)

![](img/2c41e5cacb23fe0abcd3d6b0bf88f28e_40.png)

![](img/2c41e5cacb23fe0abcd3d6b0bf88f28e_42.png)

![](img/2c41e5cacb23fe0abcd3d6b0bf88f28e_44.png)

有时我们需要从字符串中提取数据，或者将数据格式化为字符串。这时可以使用字符串流 `<sstream>`。

![](img/2c41e5cacb23fe0abcd3d6b0bf88f28e_46.png)

![](img/2c41e5cacb23fe0abcd3d6b0bf88f28e_48.png)

![](img/2c41e5cacb23fe0abcd3d6b0bf88f28e_49.png)

*   **`istringstream`**: 用于从字符串读取数据。
*   **`ostringstream`**: 用于将数据格式化为字符串。

![](img/2c41e5cacb23fe0abcd3d6b0bf88f28e_51.png)

![](img/2c41e5cacb23fe0abcd3d6b0bf88f28e_53.png)

![](img/2c41e5cacb23fe0abcd3d6b0bf88f28e_55.png)

```cpp
#include <sstream>
string data = "10 20 30";
istringstream iss(data);
int a, b, c;
iss >> a >> b >> c; // a=10, b=20, c=30
```

![](img/2c41e5cacb23fe0abcd3d6b0bf88f28e_57.png)

![](img/2c41e5cacb23fe0abcd3d6b0bf88f28e_59.png)

![](img/2c41e5cacb23fe0abcd3d6b0bf88f28e_61.png)

![](img/2c41e5cacb23fe0abcd3d6b0bf88f28e_63.png)

## 文件输入

![](img/2c41e5cacb23fe0abcd3d6b0bf88f28e_65.png)

![](img/2c41e5cacb23fe0abcd3d6b0bf88f28e_67.png)

![](img/2c41e5cacb23fe0abcd3d6b0bf88f28e_69.png)

![](img/2c41e5cacb23fe0abcd3d6b0bf88f28e_71.png)

要从文件读取数据，我们使用 `ifstream`（输入文件流）。基本步骤是：打开文件、检查是否成功打开、读取数据、关闭文件。

```cpp
ifstream inputFile;
inputFile.open("data.txt");

if (!inputFile.is_open()) {
    cout << "Failed to open file." << endl;
    return 1; // 非零返回值表示错误
}

![](img/2c41e5cacb23fe0abcd3d6b0bf88f28e_73.png)

![](img/2c41e5cacb23fe0abcd3d6b0bf88f28e_75.png)

string line;
while (getline(inputFile, line)) {
    cout << line << endl;
}

inputFile.close();
```

## 文件输出

要向文件写入数据，我们使用 `ofstream`（输出文件流）。注意，以默认方式打开文件进行写入会覆盖文件的原有内容。

```cpp
ofstream outputFile;
outputFile.open("output.txt");

![](img/2c41e5cacb23fe0abcd3d6b0bf88f28e_77.png)

![](img/2c41e5cacb23fe0abcd3d6b0bf88f28e_79.png)

if (!outputFile.is_open()) {
    cout << "Failed to open file for writing." << endl;
    return 1;
}

![](img/2c41e5cacb23fe0abcd3d6b0bf88f28e_81.png)

outputFile << "Hello, File!" << endl;
outputFile << 42 << endl;

![](img/2c41e5cacb23fe0abcd3d6b0bf88f28e_83.png)

![](img/2c41e5cacb23fe0abcd3d6b0bf88f28e_85.png)

![](img/2c41e5cacb23fe0abcd3d6b0bf88f28e_87.png)

![](img/2c41e5cacb23fe0abcd3d6b0bf88f28e_88.png)

![](img/2c41e5cacb23fe0abcd3d6b0bf88f28e_90.png)

outputFile.close();
```

## 综合示例：简易库存管理系统

![](img/2c41e5cacb23fe0abcd3d6b0bf88f28e_92.png)

上一节我们介绍了如何读写文件，本节我们来看一个综合应用：创建一个可以读取商品列表、进行销售并更新库存文件的程序。

![](img/2c41e5cacb23fe0abcd3d6b0bf88f28e_94.png)

![](img/2c41e5cacb23fe0abcd3d6b0bf88f28e_96.png)

假设我们有一个 `items.txt` 文件，格式如下（每件商品占三行：名称、价格、库存数量）：
```
Coffee
5.00
10
Coke
2.99
20
Tea
3.99
22
```

以下程序演示了如何读取该文件，处理用户购买，并写回更新后的库存文件。

![](img/2c41e5cacb23fe0abcd3d6b0bf88f28e_98.png)

```cpp
#include <iostream>
#include <fstream>
#include <string>
using namespace std;

![](img/2c41e5cacb23fe0abcd3d6b0bf88f28e_100.png)

![](img/2c41e5cacb23fe0abcd3d6b0bf88f28e_102.png)

int main() {
    string item1Name, item2Name, item3Name;
    double item1Price, item2Price, item3Price;
    int item1Qty, item2Qty, item3Qty;

    // 1. 读取文件
    ifstream inFile("items.txt");
    if (!inFile.is_open()) {
        cout << "Could not open items file. Entering manual mode." << endl;
        // ... 手动输入商品信息的代码 ...
    } else {
        getline(inFile, item1Name);
        inFile >> item1Price >> item1Qty;
        inFile.ignore(); // 忽略换行符
        getline(inFile, item2Name);
        inFile >> item2Price >> item2Qty;
        inFile.ignore();
        getline(inFile, item3Name);
        inFile >> item3Price >> item3Qty;
        inFile.close();
    }

    // 2. 显示商品并处理购买
    cout << "We sell: " << item1Name << ", " << item2Name << ", " << item3Name << endl;
    string choice;
    cout << "What do you want to buy? ";
    cin >> choice;

    // ... 确定所选商品并检查库存的代码 ...

    // 3. 更新库存并写回文件
    ofstream outFile("items.txt");
    if (outFile.is_open()) {
        outFile << item1Name << endl << item1Price << endl << item1Qty << endl;
        outFile << item2Name << endl << item2Price << endl << item2Qty << endl;
        outFile << item3Name << endl << item3Price << endl << item3Qty << endl;
        outFile.close();
        cout << "Inventory updated." << endl;
    }
    return 0;
}
```

## 文件路径

![](img/2c41e5cacb23fe0abcd3d6b0bf88f28e_104.png)

打开文件时，可以指定相对路径或绝对路径。
*   **相对路径**：相对于程序运行的当前目录。例如 `"data.txt"` 或 `"folder/data.txt"`。更具灵活性。
*   **绝对路径**：完整的系统路径。例如 `"C:\\Users\\name\\data.txt"`。通常不推荐，因为可移植性差。

## 总结

![](img/2c41e5cacb23fe0abcd3d6b0bf88f28e_106.png)

本节课我们一起学习了C++中流的核心概念，重点是如何进行文件输入输出操作。我们掌握了使用 `ifstream` 和 `ofstream` 来读写文件，了解了基本的文件操作流程（打开、检查、读写、关闭），并通过一个简易库存管理系统的例子实践了这些知识。这使得我们的程序能够持久化存储数据，功能变得更加强大。在接下来的课程中，我们将学习更复杂的数据结构来更好地管理此类信息。