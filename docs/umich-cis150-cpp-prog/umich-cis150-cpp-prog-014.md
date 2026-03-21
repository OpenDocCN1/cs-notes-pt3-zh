# 014：流操作（三）📂

![](img/c4172b75d9daff1b3143444ea32988f3_1.png)

在本节课中，我们将继续学习C++中的文件流操作。我们将探讨如何使用分隔符在单行中存储和读取多个数据项，如何以追加模式打开文件，以及如何使用向量来灵活地处理数量不定的数据。课程最后，我们会回顾期中考试的相关安排。

---

![](img/c4172b75d9daff1b3143444ea32988f3_3.png)

![](img/c4172b75d9daff1b3143444ea32988f3_5.png)

![](img/c4172b75d9daff1b3143444ea32988f3_7.png)

## 文件读写与分隔符

上一节我们学习了如何按行读写文件。本节中我们来看看如何将多个数据项存储在一行中，并使用特定的字符（分隔符）将它们分开。

这种方法在数据格式紧凑时非常有用。例如，我们可以将商店名和购物清单中的所有物品写在同一行，用“|”字符分隔。

以下是写入文件的代码示例：
```cpp
#include <fstream>
#include <string>
using namespace std;

int main() {
    ofstream outFile;
    outFile.open("list.txt");
    outFile << "Kroger|Milk|Lettuce|Eggs" << endl;
    outFile.close();
    return 0;
}
```
这段代码创建了一个名为`list.txt`的文件，并将字符串`Kroger|Milk|Lettuce|Eggs`写入其中。

![](img/c4172b75d9daff1b3143444ea32988f3_9.png)

---

![](img/c4172b75d9daff1b3143444ea32988f3_11.png)

## 从文件中读取并解析数据

![](img/c4172b75d9daff1b3143444ea32988f3_13.png)

![](img/c4172b75d9daff1b3143444ea32988f3_15.png)

写入数据后，我们需要能够将其读回程序。这涉及到读取整行字符串，然后根据分隔符将其拆分成独立的部分。

以下是读取并解析文件的步骤：
1.  打开文件进行读取。
2.  使用`getline`函数读取一整行。
3.  使用`find`函数在字符串中定位分隔符的位置。
4.  使用`substr`函数根据分隔符的位置提取子字符串。

![](img/c4172b75d9daff1b3143444ea32988f3_17.png)

![](img/c4172b75d9daff1b3143444ea32988f3_19.png)

以下是实现该过程的代码示例：
```cpp
#include <fstream>
#include <string>
#include <iostream>
using namespace std;

![](img/c4172b75d9daff1b3143444ea32988f3_21.png)

![](img/c4172b75d9daff1b3143444ea32988f3_22.png)

![](img/c4172b75d9daff1b3143444ea32988f3_24.png)

![](img/c4172b75d9daff1b3143444ea32988f3_26.png)

int main() {
    ifstream inFile;
    inFile.open("list.txt");
    string line;
    getline(inFile, line); // 读取整行

    char delimiter = '|';
    size_t index = 0;
    size_t nextIndex = line.find(delimiter);

    // 提取商店名（第一个分隔符之前的部分）
    string storeName = line.substr(0, nextIndex);
    cout << "Store: " << storeName << endl;

    // 循环提取所有物品
    while (nextIndex != string::npos) {
        index = nextIndex + 1; // 移动到分隔符之后
        nextIndex = line.find(delimiter, index); // 查找下一个分隔符

        // 提取一个物品
        string item = line.substr(index, nextIndex - index);
        if (!item.empty()) {
            cout << "Item: " << item << endl;
        }
    }

    inFile.close();
    return 0;
}
```
这段代码会输出商店名和所有以“|”分隔的物品。

![](img/c4172b75d9daff1b3143444ea32988f3_28.png)

---

![](img/c4172b75d9daff1b3143444ea32988f3_30.png)

![](img/c4172b75d9daff1b3143444ea32988f3_32.png)

![](img/c4172b75d9daff1b3143444ea32988f3_34.png)

## 使用向量存储动态数量的数据

![](img/c4172b75d9daff1b3143444ea32988f3_35.png)

![](img/c4172b75d9daff1b3143444ea32988f3_37.png)

上面的例子假设我们知道有多少个物品。为了更灵活地处理任意数量的数据项，我们可以使用`vector`容器。

![](img/c4172b75d9daff1b3143444ea32988f3_39.png)

向量可以动态地存储多个同类型的数据项，我们无需在编写代码时确定其具体数量。

![](img/c4172b75d9daff1b3143444ea32988f3_41.png)

以下是使用向量改进后的读取代码：
```cpp
#include <fstream>
#include <string>
#include <vector>
#include <iostream>
using namespace std;

int main() {
    ifstream inFile;
    inFile.open("list.txt");
    string line;
    getline(inFile, line);

    char delimiter = '|';
    vector<string> items;
    size_t index = 0;
    size_t nextIndex = line.find(delimiter);

    // 第一个部分是商店名
    string storeName = line.substr(0, nextIndex);

    // 循环提取所有物品并存入向量
    while (nextIndex != string::npos) {
        index = nextIndex + 1;
        nextIndex = line.find(delimiter, index);
        string item = line.substr(index, nextIndex - index);
        if (!item.empty()) {
            items.push_back(item); // 将物品添加到向量末尾
        }
    }

    cout << "List for " << storeName << ":" << endl;
    for (const string& item : items) {
        cout << "- " << item << endl;
    }

    inFile.close();
    return 0;
}
```
现在，无论一行中有多少个物品，代码都能正确读取并存储它们。

![](img/c4172b75d9daff1b3143444ea32988f3_43.png)

---

![](img/c4172b75d9daff1b3143444ea32988f3_45.png)

![](img/c4172b75d9daff1b3143444ea32988f3_47.png)

![](img/c4172b75d9daff1b3143444ea32988f3_49.png)

![](img/c4172b75d9daff1b3143444ea32988f3_51.png)

![](img/c4172b75d9daff1b3143444ea32988f3_53.png)

## 以追加模式打开文件

默认情况下，用`ofstream`打开文件会覆盖原有内容。如果我们想在不删除旧数据的情况下添加新内容，可以使用追加模式。

![](img/c4172b75d9daff1b3143444ea32988f3_55.png)

![](img/c4172b75d9daff1b3143444ea32988f3_57.png)

![](img/c4172b75d9daff1b3143444ea32988f3_59.png)

以下是使用追加模式打开文件的代码：
```cpp
ofstream outFile;
outFile.open("list.txt", ios::app); // ios::app 表示追加模式
outFile << "Gamestop|Battlefield|GTA|Ghost of Tsushima" << endl;
outFile.close();
```
运行此代码后，新的购物清单会被添加到`list.txt`文件的末尾，而不会清除“Kroger”的那条记录。

![](img/c4172b75d9daff1b3143444ea32988f3_61.png)

![](img/c4172b75d9daff1b3143444ea32988f3_62.png)

![](img/c4172b75d9daff1b3143444ea32988f3_64.png)

![](img/c4172b75d9daff1b3143444ea32988f3_66.png)

![](img/c4172b75d9daff1b3143444ea32988f3_68.png)

---

## 调试技巧

在编写文件解析代码时，很容易遇到索引错误或逻辑问题。使用调试器是解决这类问题的最佳方法。

![](img/c4172b75d9daff1b3143444ea32988f3_70.png)

以下是简单的调试步骤：
1.  在可能出错的代码行设置断点。
2.  逐行执行程序。
3.  观察变量（如`index`、`nextIndex`、`line`）的值是否符合预期。
4.  根据观察结果调整代码逻辑。

---

## 期中考试安排与复习

本节课的最后，我们来看看期中考试的安排。考试将于指定日期在Canvas平台以线上测验形式进行。

以下是考试的基本信息：
*   **形式**：开卷、开笔记、可查阅资料。
*   **内容**：包含选择题、简答题和编程题。
*   **要求**：所有提交的答案必须是个人独立完成，引用外部资源需注明出处。

为了帮助大家复习，上一学期的期中试卷已作为练习题提供。建议先尝试独立完成，再看讲解。

---

![](img/c4172b75d9daff1b3143444ea32988f3_72.png)

![](img/c4172b75d9daff1b3143444ea32988f3_74.png)

![](img/c4172b75d9daff1b3143444ea32988f3_76.png)

![](img/c4172b75d9daff1b3143444ea32988f3_77.png)

## 课程总结

![](img/c4172b75d9daff1b3143444ea32988f3_79.png)

本节课中我们一起学习了C++文件流操作的高级技巧。我们掌握了如何使用分隔符在一行内组织数据、如何读取并解析这种格式的数据、如何使用`vector`来灵活处理数据集合，以及如何以追加模式向文件添加内容。此外，我们还介绍了使用调试器排查代码问题的方法，并了解了期中考试的相关信息。掌握这些技能将帮助你更有效地在程序中处理持久化数据。