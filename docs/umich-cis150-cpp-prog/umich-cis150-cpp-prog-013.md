# 013：流（第二部分）📂

![](img/d2cadc6e5c62aff90d8f828238d53841_1.png)

在本节课中，我们将学习C++中关于流（Streams）的更多知识，特别是如何与文件进行交互。我们将了解输入/输出流、字符串流，并最终学习如何从文件中读取数据以及向文件中写入数据。

---

## 输入与输出流回顾 🔄

![](img/d2cadc6e5c62aff90d8f828238d53841_3.png)

![](img/d2cadc6e5c62aff90d8f828238d53841_5.png)

上一节我们介绍了流的基本概念。本节中，我们来看看我们一直在使用的两种标准流：`cin`（标准输入流）和 `cout`（标准输出流）。

![](img/d2cadc6e5c62aff90d8f828238d53841_7.png)

![](img/d2cadc6e5c62aff90d8f828238d53841_9.png)

![](img/d2cadc6e5c62aff90d8f828238d53841_11.png)

![](img/d2cadc6e5c62aff90d8f828238d53841_13.png)

![](img/d2cadc6e5c62aff90d8f828238d53841_15.png)

*   `cout` 是输出流。我们使用**插入运算符** `<<` 将数据插入到输出流中，数据随后会显示在控制台。
    ```cpp
    cout << "Hello, World!";
    ```
*   `cin` 是输入流。我们使用**提取运算符** `>>` 从输入流中提取用户输入的数据。
    ```cpp
    int number;
    cin >> number;
    ```

![](img/d2cadc6e5c62aff90d8f828238d53841_17.png)

![](img/d2cadc6e5c62aff90d8f828238d53841_19.png)

![](img/d2cadc6e5c62aff90d8f828238d53841_21.png)

---

![](img/d2cadc6e5c62aff90d8f828238d53841_23.png)

![](img/d2cadc6e5c62aff90d8f828238d53841_24.png)

## 处理整行输入 📝

![](img/d2cadc6e5c62aff90d8f828238d53841_26.png)

![](img/d2cadc6e5c62aff90d8f828238d53841_28.png)

![](img/d2cadc6e5c62aff90d8f828238d53841_30.png)

![](img/d2cadc6e5c62aff90d8f828238d53841_32.png)

当我们需要获取包含空格的整行文本（例如全名）时，使用 `cin >>` 会遇到问题，因为它会在遇到空格时停止提取。

![](img/d2cadc6e5c62aff90d8f828238d53841_34.png)

![](img/d2cadc6e5c62aff90d8f828238d53841_35.png)

![](img/d2cadc6e5c62aff90d8f828238d53841_36.png)

![](img/d2cadc6e5c62aff90d8f828238d53841_38.png)

![](img/d2cadc6e5c62aff90d8f828238d53841_40.png)

![](img/d2cadc6e5c62aff90d8f828238d53841_42.png)

以下是处理整行输入的方法：
```cpp
string fullName;
getline(cin, fullName); // 获取整行输入，包括空格，直到遇到回车键
```

![](img/d2cadc6e5c62aff90d8f828238d53841_44.png)

![](img/d2cadc6e5c62aff90d8f828238d53841_46.png)

![](img/d2cadc6e5c62aff90d8f828238d53841_48.png)

![](img/d2cadc6e5c62aff90d8f828238d53841_50.png)

**注意**：混合使用 `cin >>` 和 `getline()` 可能导致意外行为，因为 `cin >>` 会留下换行符在输入流中。一个简单的解决方法是使用一个额外的 `getline()` 来“消耗”这个换行符。

![](img/d2cadc6e5c62aff90d8f828238d53841_52.png)

![](img/d2cadc6e5c62aff90d8f828238d53841_54.png)

---

## 字符串流：解析字符串数据 🧵

字符串流允许我们将一个字符串当作流来处理，从而可以方便地从中提取格式化的数据。这在处理从文件读取的整行数据时非常有用。

![](img/d2cadc6e5c62aff90d8f828238d53841_56.png)

![](img/d2cadc6e5c62aff90d8f828238d53841_57.png)

以下是使用输入字符串流 (`istringstream`) 的步骤：
1.  包含头文件 `<sstream>`。
2.  创建一个 `istringstream` 对象，并用一个字符串初始化它。
3.  像使用 `cin` 一样，使用 `>>` 运算符从这个流中提取数据。

![](img/d2cadc6e5c62aff90d8f828238d53841_59.png)

```cpp
#include <sstream>
#include <string>
using namespace std;

![](img/d2cadc6e5c62aff90d8f828238d53841_61.png)

string vehicleInfo = "2011 Ford Fiesta";
istringstream iss(vehicleInfo); // 创建字符串输入流

![](img/d2cadc6e5c62aff90d8f828238d53841_63.png)

string year, make, model;
iss >> year >> make >> model; // 从字符串流中提取数据

![](img/d2cadc6e5c62aff90d8f828238d53841_65.png)

![](img/d2cadc6e5c62aff90d8f828238d53841_67.png)

![](img/d2cadc6e5c62aff90d8f828238d53841_69.png)

![](img/d2cadc6e5c62aff90d8f828238d53841_71.png)

![](img/d2cadc6e5c62aff90d8f828238d53841_73.png)

![](img/d2cadc6e5c62aff90d8f828238d53841_75.png)

cout << "Year: " << year << ", Make: " << make << ", Model: " << model << endl;
```

![](img/d2cadc6e5c62aff90d8f828238d53841_77.png)

![](img/d2cadc6e5c62aff90d8f828238d53841_79.png)

---

![](img/d2cadc6e5c62aff90d8f828238d53841_81.png)

![](img/d2cadc6e5c62aff90d8f828238d53841_83.png)

## 输出字符串流：构建字符串 🛠️

输出字符串流 (`ostringstream`) 允许我们像使用 `cout` 一样构建一个字符串，而不是直接输出到控制台。这对于格式化要写入文件或进行其他处理的字符串非常有用。

![](img/d2cadc6e5c62aff90d8f828238d53841_85.png)

![](img/d2cadc6e5c62aff90d8f828238d53841_87.png)

![](img/d2cadc6e5c62aff90d8f828238d53841_89.png)

```cpp
#include <sstream>
using namespace std;

![](img/d2cadc6e5c62aff90d8f828238d53841_91.png)

ostringstream oss; // 创建字符串输出流
oss << "The result is: " << 42 << " and " << 3.14;

![](img/d2cadc6e5c62aff90d8f828238d53841_93.png)

string finalString = oss.str(); // 获取构建好的字符串
cout << finalString << endl; // 输出：The result is: 42 and 3.14
```

![](img/d2cadc6e5c62aff90d8f828238d53841_95.png)

![](img/d2cadc6e5c62aff90d8f828238d53841_97.png)

![](img/d2cadc6e5c62aff90d8f828238d53841_99.png)

---

![](img/d2cadc6e5c62aff90d8f828238d53841_101.png)

![](img/d2cadc6e5c62aff90d8f828238d53841_103.png)

![](img/d2cadc6e5c62aff90d8f828238d53841_105.png)

## 文件操作：读取文件 📖

![](img/d2cadc6e5c62aff90d8f828238d53841_107.png)

现在，我们进入核心部分：文件操作。使用文件可以让我们处理持久化数据，而不仅仅是在程序运行时存在于内存中的数据。

![](img/d2cadc6e5c62aff90d8f828238d53841_109.png)

处理文件通常遵循三个步骤：**打开文件**、**读取/写入文件**、**关闭文件**。

![](img/d2cadc6e5c62aff90d8f828238d53841_111.png)

以下是读取文件的基本步骤：
1.  包含头文件 `<fstream>`。
2.  创建一个 `ifstream`（输入文件流）对象。
3.  使用 `.open()` 方法打开文件。
4.  检查文件是否成功打开。
5.  使用 `>>` 或 `getline()` 从文件流中读取数据。
6.  使用 `.close()` 方法关闭文件。

```cpp
#include <fstream>
#include <iostream>
using namespace std;

![](img/d2cadc6e5c62aff90d8f828238d53841_113.png)

![](img/d2cadc6e5c62aff90d8f828238d53841_115.png)

![](img/d2cadc6e5c62aff90d8f828238d53841_117.png)

![](img/d2cadc6e5c62aff90d8f828238d53841_119.png)

int main() {
    ifstream inputFile; // 创建输入文件流对象
    inputFile.open("data.txt"); // 打开名为"data.txt"的文件

    // 检查文件是否成功打开
    if (!inputFile.is_open()) {
        cout << "Could not open file data.txt" << endl;
        return 1; // 返回非零值表示错误
    }

    int value;
    // 从文件中读取一个整数
    inputFile >> value;
    cout << "Read value: " << value << endl;

    inputFile.close(); // 关闭文件
    return 0;
}
```

![](img/d2cadc6e5c62aff90d8f828238d53841_121.png)

![](img/d2cadc6e5c62aff90d8f828238d53841_123.png)

**重要概念：文件路径**
*   **相对路径**：如 `"data.txt"`。程序会在其**运行目录**中寻找该文件。在集成开发环境（如Visual Studio）中运行时，这通常是项目目录。这是最常用和可移植的方式。
*   **绝对路径**：如 `"C:\\Users\\Name\\data.txt"`（注意Windows中需要使用双反斜杠`\\`）。指定了文件的完整位置，但程序移植到其他计算机时可能失效。

![](img/d2cadc6e5c62aff90d8f828238d53841_125.png)

---

## 读取文件中的所有数据 🔄

![](img/d2cadc6e5c62aff90d8f828238d53841_127.png)

![](img/d2cadc6e5c62aff90d8f828238d53841_129.png)

![](img/d2cadc6e5c62aff90d8f828238d53841_131.png)

![](img/d2cadc6e5c62aff90d8f828238d53841_133.png)

![](img/d2cadc6e5c62aff90d8f828238d53841_134.png)

我们通常需要读取文件中的多个数据，直到文件末尾。这可以通过循环来实现。

![](img/d2cadc6e5c62aff90d8f828238d53841_136.png)

![](img/d2cadc6e5c62aff90d8f828238d53841_138.png)

![](img/d2cadc6e5c62aff90d8f828238d53841_140.png)

```cpp
#include <fstream>
#include <iostream>
using namespace std;

![](img/d2cadc6e5c62aff90d8f828238d53841_142.png)

![](img/d2cadc6e5c62aff90d8f828238d53841_143.png)

int main() {
    ifstream inputFile("numbers.txt"); // 创建并打开文件（构造函数方式）

    if (!inputFile) { // 更简洁的打开检查方式
        cerr << "Error opening file." << endl;
        return 1;
    }

    int number;
    int total = 0;

    // 当可以成功从文件中提取一个整数时，继续循环
    while (inputFile >> number) {
        total += number;
        cout << "Read: " << number << endl;
    }

    // 循环结束后，检查是否正常到达文件末尾
    if (inputFile.eof()) {
        cout << "End of file reached successfully." << endl;
    } else {
        cout << "Error reading file before reaching the end." << endl;
    }

    cout << "Total sum: " << total << endl;

    inputFile.close();
    return 0;
}
```

![](img/d2cadc6e5c62aff90d8f828238d53841_145.png)

---

![](img/d2cadc6e5c62aff90d8f828238d53841_147.png)

![](img/d2cadc6e5c62aff90d8f828238d53841_149.png)

## 总结 📚

![](img/d2cadc6e5c62aff90d8f828238d53841_151.png)

![](img/d2cadc6e5c62aff90d8f828238d53841_153.png)

![](img/d2cadc6e5c62aff90d8f828238d53841_155.png)

本节课中我们一起学习了C++流的高级应用：
1.  回顾了标准输入/输出流 (`cin`/`cout`)。
2.  学习了如何使用 `getline()` 获取整行输入，并注意了与 `cin >>` 混用时的陷阱。
3.  掌握了**字符串流** (`istringstream` 和 `ostringstream`) 的用法，用于解析字符串和构建字符串。
4.  重点学习了**文件输入**操作，包括如何打开文件、检查状态、读取数据（单个或全部）以及正确关闭文件。
5.  理解了相对路径和绝对路径的区别。

![](img/d2cadc6e5c62aff90d8f828238d53841_157.png)

![](img/d2cadc6e5c62aff90d8f828238d53841_158.png)

![](img/d2cadc6e5c62aff90d8f828238d53841_159.png)

![](img/d2cadc6e5c62aff90d8f828238d53841_160.png)

![](img/d2cadc6e5c62aff90d8f828238d53841_161.png)

![](img/d2cadc6e5c62aff90d8f828238d53841_163.png)

![](img/d2cadc6e5c62aff90d8f828238d53841_165.png)

![](img/d2cadc6e5c62aff90d8f828238d53841_167.png)

文件操作是程序与外部世界交互的关键，它使得数据处理变得自动化且高效。在接下来的课程中，我们将学习如何向文件中写入数据。