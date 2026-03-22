# 015：迭代器适配器 part2 🚀

![](img/6db8f2471826fc6bae54a3b911133c48_1.png)

![](img/6db8f2471826fc6bae54a3b911133c48_3.png)

在本节课中，我们将继续学习迭代器适配器，重点介绍所谓的“流适配器”。这些适配器允许我们将输入/输出流对象无缝地集成到各种STL算法中，使它们像迭代器一样工作。

## 概述 📋

![](img/6db8f2471826fc6bae54a3b911133c48_5.png)

上一节我们介绍了迭代器适配器的基本概念。本节中，我们将深入探讨三种流适配器：**istream_iterator**、**ostream_iterator** 和 **istreambuf_iterator**。我们将通过具体示例，学习如何利用它们简化数据从流到容器，以及从容器到流的处理过程。

![](img/6db8f2471826fc6bae54a3b911133c48_7.png)

---

![](img/6db8f2471826fc6bae54a3b911133c48_9.png)

![](img/6db8f2471826fc6bae54a3b911133c48_10.png)

## 示例1：使用istream和ostream适配器 📥📤

![](img/6db8f2471826fc6bae54a3b911133c48_12.png)

![](img/6db8f2471826fc6bae54a3b911133c48_13.png)

![](img/6db8f2471826fc6bae54a3b911133c48_15.png)

![](img/6db8f2471826fc6bae54a3b911133c48_16.png)

第一个示例将演示如何使用 `istream_iterator` 和 `ostream_iterator` 适配器。其核心思想是，我们无需显式地从流中提取或插入数据，而是使用流适配器让流表现得像STL容器一样。然后，我们可以使用 `copy` 等算法来管理构建容器的过程。

![](img/6db8f2471826fc6bae54a3b911133c48_18.png)

![](img/6db8f2471826fc6bae54a3b911133c48_19.png)

![](img/6db8f2471826fc6bae54a3b911133c48_20.png)

以下是该示例的关键步骤：

1.  **创建空容器**：我们首先创建一个空的 `list<string>`。
2.  **使用istream_iterator读取**：我们应用 `istream_iterator` 适配器到 `cin`，将其作为输入迭代器来读取字符串。
3.  **插入到容器**：使用 `copy` 算法，将从标准输入读取的每个字符串，通过 `back_inserter` 迭代器适配器插入到列表的末尾。
4.  **排序容器**：由于 `list` 是双向迭代器容器，我们使用其成员函数 `sort()` 进行排序。
5.  **使用ostream_iterator输出**：最后，我们再次使用 `copy` 算法，将排序后的列表内容通过 `ostream_iterator` 适配器输出到 `cout`，每个元素后跟一个换行符。

![](img/6db8f2471826fc6bae54a3b911133c48_22.png)

**核心概念代码描述**：
```cpp
// 从标准输入读取字符串到列表
list<string> myList;
copy(istream_iterator<string>(cin), istream_iterator<string>(), back_inserter(myList));

![](img/6db8f2471826fc6bae54a3b911133c48_24.png)

![](img/6db8f2471826fc6bae54a3b911133c48_25.png)

// 对列表排序（使用成员函数）
myList.sort();

// 将列表内容输出到标准输出，以换行分隔
copy(myList.begin(), myList.end(), ostream_iterator<string>(cout, "\n"));
```

![](img/6db8f2471826fc6bae54a3b911133c48_27.png)

![](img/6db8f2471826fc6bae54a3b911133c48_28.png)

![](img/6db8f2471826fc6bae54a3b911133c48_30.png)

**运行示例**：
输入：`now is the time for all good people to come to the aid of their party!`
输出：（按字母顺序排序后的所有单词）

![](img/6db8f2471826fc6bae54a3b911133c48_32.png)

![](img/6db8f2471826fc6bae54a3b911133c48_34.png)

这个示例展示了如何轻松地将流适配器与 `copy` 算法及其他迭代器适配器（如 `back_inserter`）结合使用。

![](img/6db8f2471826fc6bae54a3b911133c48_36.png)

---

## 示例2：显式使用流迭代器与accumulate算法 🧮

![](img/6db8f2471826fc6bae54a3b911133c48_38.png)

![](img/6db8f2471826fc6bae54a3b911133c48_40.png)

![](img/6db8f2471826fc6bae54a3b911133c48_41.png)

第二个示例将进一步演示相关概念，并更显式地使用 `istream_iterator` 和 `ostream_iterator`。我们还将引入 `accumulate` 算法来计算总和。

![](img/6db8f2471826fc6bae54a3b911133c48_43.png)

![](img/6db8f2471826fc6bae54a3b911133c48_45.png)

以下是该示例的关键步骤：

![](img/6db8f2471826fc6bae54a3b911133c48_47.png)

![](img/6db8f2471826fc6bae54a3b911133c48_49.png)

1.  **创建显式迭代器对象**：我们显式创建名为 `ii` 的 `istream_iterator<int>` 和名为 `oi` 的 `ostream_iterator<int>`。
2.  **读取数据到向量**：使用 `copy` 算法和 `back_inserter`，从 `ii`（绑定到 `cin`）读取整数，直到遇到文件结束符，并将它们存入一个 `vector<int>`。
3.  **输出除最后一个外的所有元素**：再次使用 `copy` 算法，将向量中除最后一个元素外的所有内容输出到 `oi`（绑定到 `cout`），元素间用空格分隔。
4.  **手动输出最后一个元素并计算总和**：我们手动输出向量的最后一个元素，然后使用 `accumulate` 算法计算向量中所有整数的总和并输出。

![](img/6db8f2471826fc6bae54a3b911133c48_51.png)

![](img/6db8f2471826fc6bae54a3b911133c48_52.png)

![](img/6db8f2471826fc6bae54a3b911133c48_53.png)

**核心概念代码描述**：
```cpp
// 显式创建流迭代器
istream_iterator<int> ii(cin);
ostream_iterator<int> oi(cout, " ");
istream_iterator<int> eos; // 表示流结束

![](img/6db8f2471826fc6bae54a3b911133c48_55.png)

vector<int> v;
// 读取输入
copy(ii, eos, back_inserter(v));

![](img/6db8f2471826fc6bae54a3b911133c48_57.png)

if (!v.empty()) {
    // 输出除最后一个外的所有元素
    copy(v.begin(), v.end() - 1, oi);
    // 输出最后一个元素和总和
    cout << v.back() << "\nSum is " << accumulate(v.begin(), v.end(), 0) << endl;
}
```

**运行示例**：
输入：`10 20 30 40 50 60` (后跟EOF)
输出：`10 20 30 40 50 60 Sum is 210`

![](img/6db8f2471826fc6bae54a3b911133c48_59.png)

![](img/6db8f2471826fc6bae54a3b911133c48_60.png)

这个示例不仅展示了显式使用流迭代器，还演示了如何与 `accumulate` 这样的数值算法配合使用。

![](img/6db8f2471826fc6bae54a3b911133c48_62.png)

---

![](img/6db8f2471826fc6bae54a3b911133c48_63.png)

![](img/6db8f2471826fc6bae54a3b911133c48_64.png)

![](img/6db8f2471826fc6bae54a3b911133c48_66.png)

![](img/6db8f2471826fc6bae54a3b911133c48_68.png)

## 示例3：深入ostream_iterator适配器 ✍️

![](img/6db8f2471826fc6bae54a3b911133c48_70.png)

第三个示例主要聚焦于 `ostream_iterator` 适配器的使用细节。

![](img/6db8f2471826fc6bae54a3b911133c48_72.png)

以下是该示例的关键步骤：

![](img/6db8f2471826fc6bae54a3b911133c48_74.png)

![](img/6db8f2471826fc6bae54a3b911133c48_76.png)

![](img/6db8f2471826fc6bae54a3b911133c48_77.png)

1.  **直接赋值输出**：我们创建一个 `ostream_iterator<int>`，并直接通过赋值操作符 (`=`) 向其写入值（如6和88）。这触发了适配器内部的输出操作。
2.  **处理容器输出**：我们创建一个 `deque` 并填充数据。使用 `copy` 算法将 `deque` 中除最后一个元素外的所有内容输出到另一个 `ostream_iterator`，这次我们指定加号 (`+`) 作为分隔符。
3.  **输出最后一个元素与求和**：手动输出最后一个元素，然后使用 `accumulate` 计算总和。

**核心概念代码描述**：
```cpp
// 创建带空格分隔符的ostream_iterator并直接赋值
ostream_iterator<int> oi1(cout, " ");
oi1 = 6; // 输出 "6 "
oi1 = 88; // 输出 "88 "

deque<int> d = {3, 4, 7, 8};
// 创建带加号分隔符的ostream_iterator
ostream_iterator<int> oi2(cout, "+");
// 输出除最后一个外的元素
copy(d.begin(), d.end() - 1, oi2);
// 输出最后一个元素和总和
cout << d.back() << "\nSum is " << accumulate(d.begin(), d.end(), 0) << endl;
```

![](img/6db8f2471826fc6bae54a3b911133c48_79.png)

**运行示例**：
输出：`6 88 3+4+7+8 Sum is 22`

![](img/6db8f2471826fc6bae54a3b911133c48_81.png)

![](img/6db8f2471826fc6bae54a3b911133c48_83.png)

这个示例强调了 `ostream_iterator` 如何通过赋值操作进行写操作，以及如何自定义输出分隔符。

![](img/6db8f2471826fc6bae54a3b911133c48_85.png)

![](img/6db8f2471826fc6bae54a3b911133c48_87.png)

---

![](img/6db8f2471826fc6bae54a3b911133c48_89.png)

## 示例4：使用istreambuf_iterator进行底层字符操作 🔧

![](img/6db8f2471826fc6bae54a3b911133c48_91.png)

最后一个示例介绍更底层的 `istreambuf_iterator` 适配器，它用于从流缓冲区读取或写入单个字符。

以下是该示例的关键步骤：

![](img/6db8f2471826fc6bae54a3b911133c48_93.png)

1.  **写入文件**：程序创建一个临时文件，并向其中写入一个字符串。
2.  **重置文件指针**：将文件读指针移回开头。
3.  **使用istreambuf_iterator读取**：创建一个 `istreambuf_iterator<char>` 绑定到该文件的读缓冲区，用于逐个字符读取文件内容。
4.  **输出到屏幕**：
    *   **方法A（手动迭代）**：通过循环，解引用迭代器获取字符并输出，然后递增迭代器。
    *   **方法B（使用copy算法）**：更简洁的方式是直接使用 `copy` 算法，将 `istreambuf_iterator` 作为输入，`ostream_iterator<char>` 作为输出，一次性完成复制。

![](img/6db8f2471826fc6bae54a3b911133c48_95.png)

**核心概念代码描述**：
```cpp
// 方法A：手动循环
istreambuf_iterator<char> in_begin(file.rdbuf());
istreambuf_iterator<char> in_end;
while (in_begin != in_end) {
    cout << *in_begin;
    ++in_begin;
}

![](img/6db8f2471826fc6bae54a3b911133c48_97.png)

// 方法B：使用copy算法（更简洁）
copy(istreambuf_iterator<char>(file.rdbuf()),
     istreambuf_iterator<char>(),
     ostream_iterator<char>(cout));
```

![](img/6db8f2471826fc6bae54a3b911133c48_99.png)

![](img/6db8f2471826fc6bae54a3b911133c48_101.png)

**运行示例**：
输出：`Here is a sample sentence for output. I hope you like this sentence out there.`

![](img/6db8f2471826fc6bae54a3b911133c48_102.png)

![](img/6db8f2471826fc6bae54a3b911133c48_104.png)

这个示例展示了 `istreambuf_iterator` 在处理原始字符流时的强大能力，特别是在需要绕过格式化操作、直接访问底层缓冲区时非常有用。

![](img/6db8f2471826fc6bae54a3b911133c48_106.png)

---

![](img/6db8f2471826fc6bae54a3b911133c48_108.png)

![](img/6db8f2471826fc6bae54a3b911133c48_110.png)

## 总结 🎯

![](img/6db8f2471826fc6bae54a3b911133c48_112.png)

本节课中我们一起学习了三种强大的流迭代器适配器：

![](img/6db8f2471826fc6bae54a3b911133c48_114.png)

1.  **`istream_iterator`**：将输入流适配为输入迭代器，用于从流（如 `cin`、文件流）中读取格式化数据（如 `int`， `string`）。
2.  **`ostream_iterator`**：将输出流适配为输出迭代器，用于向流（如 `cout`、文件流）中写入格式化数据，并可指定分隔符。
3.  **`istreambuf_iterator`**：提供对流缓冲区的底层访问，用于逐个字符地读取或写入数据，不进行格式化处理。

这些适配器完美体现了STL的“正交性”和“可适配性”设计理念。通过将它们与 `copy`、`accumulate` 等算法以及 `back_inserter` 等插入迭代器结合，我们可以用极简且表达力强的代码完成复杂的流与容器间的数据交换任务，极大地提升了代码的简洁性和可读性。