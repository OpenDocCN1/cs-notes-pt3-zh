# 005：向量进阶 🚀

![](img/0b1fc2c8dbc4dd9e9c6cc85820740939_0.png)

![](img/0b1fc2c8dbc4dd9e9c6cc85820740939_2.png)

在本节课中，我们将深入学习C++中向量的高级操作。我们将探讨如何遍历向量、使用迭代器以及动态地添加和删除元素。通过实践，你将掌握如何更灵活地操作向量，为后续的数据结构学习打下坚实基础。

![](img/0b1fc2c8dbc4dd9e9c6cc85820740939_4.png)


---

## 向量遍历的多种方式 🔄

上一节我们介绍了向量的基本操作，本节中我们来看看如何遍历向量。有多种方法可以遍历向量中的元素，每种方法都有其适用场景。


![](img/0b1fc2c8dbc4dd9e9c6cc85820740939_9.png)

### 1. 基于范围的for循环（只读）
这种方法简洁明了，适用于只需要读取向量元素而不修改它们的情况。

```cpp
for (string course : classes) {
    cout << course << endl;
}
```



### 2. 使用索引的for循环（可修改）
如果你需要在遍历时修改向量中的元素，可以使用传统的索引循环。

![](img/0b1fc2c8dbc4dd9e9c6cc85820740939_15.png)

```cpp
for (int index = 0; index < classes.size(); index++) {
    cout << classes.at(index) << endl;
    // 可以在此处修改 classes.at(index)
}
```

![](img/0b1fc2c8dbc4dd9e9c6cc85820740939_17.png)

### 3. 使用迭代器（灵活且功能强大）
迭代器提供了更底层的控制，允许你在遍历过程中进行插入、删除等操作。以下是使用迭代器的基本步骤：

```cpp
// 声明一个指向向量开头的迭代器
vector<string>::iterator it = classes.begin();
// 循环直到迭代器到达向量末尾
while (it != classes.end()) {
    // 解引用迭代器以获取当前元素
    cout << *it << endl;
    // 将迭代器移动到下一个元素
    it++;
}
```

为了简化代码，可以使用 `auto` 关键字让编译器自动推断迭代器类型。


```cpp
for (auto it = classes.begin(); it != classes.end(); it++) {
    cout << *it << endl;
}
```


---

## 动态操作向量元素 🛠️

![](img/0b1fc2c8dbc4dd9e9c6cc85820740939_23.png)

![](img/0b1fc2c8dbc4dd9e9c6cc85820740939_25.png)

掌握了遍历方法后，我们来看看如何动态地向向量中添加和删除元素。

### 添加元素
使用 `push_back` 方法可以向向量末尾添加新元素。

![](img/0b1fc2c8dbc4dd9e9c6cc85820740939_27.png)

![](img/0b1fc2c8dbc4dd9e9c6cc85820740939_29.png)


```cpp
string input;
while (input != "quit") {
    cout << "Enter a class (or 'quit' to finish): ";
    getline(cin, input);
    if (input != "quit") {
        classes.push_back(input);
    }
}
```


### 删除特定元素
要从向量中删除特定元素，我们需要先找到该元素的位置（使用迭代器），然后调用 `erase` 方法。

以下是删除特定课程的步骤：



1.  获取用户想要删除的课程名称。
2.  遍历向量，查找匹配的课程。
3.  保存找到的迭代器位置。
4.  在循环结束后，使用保存的迭代器删除该元素。

![](img/0b1fc2c8dbc4dd9e9c6cc85820740939_39.png)

![](img/0b1fc2c8dbc4dd9e9c6cc85820740939_41.png)


![](img/0b1fc2c8dbc4dd9e9c6cc85820740939_43.png)

![](img/0b1fc2c8dbc4dd9e9c6cc85820740939_45.png)




```cpp
cout << "Which class do you want to drop? ";
string classToDrop;
getline(cin, classToDrop);
vector<string>::iterator toErase; // 用于保存要删除元素的迭代器
bool found = false;
// 遍历查找
for (auto it = classes.begin(); it != classes.end(); it++) {
    if (*it == classToDrop) {
        toErase = it; // 保存位置
        found = true;
        break; // 找到第一个匹配项后就退出循环
    }
}

// 如果找到，则删除
if (found) {
    classes.erase(toErase);
    cout << "Class dropped." << endl;
} else {
    cout << "Class not found." << endl;
}
```


![](img/0b1fc2c8dbc4dd9e9c6cc85820740939_53.png)

![](img/0b1fc2c8dbc4dd9e9c6cc85820740939_55.png)

**重要提示**：在循环内部直接调用 `erase(it)` 会使当前迭代器失效，导致程序崩溃。因此，需要先保存迭代器，在循环外部进行删除操作。





---






## 向量与数组的对比 📊


![](img/0b1fc2c8dbc4dd9e9c6cc85820740939_77.png)

在结束之前，我们来简单对比一下向量和传统数组。

![](img/0b1fc2c8dbc4dd9e9c6cc85820740939_79.png)

![](img/0b1fc2c8dbc4dd9e9c6cc85820740939_81.png)

*   **灵活性**：向量可以动态调整大小（使用 `push_back`、`erase` 等），而数组的大小是固定的。
*   **内存管理**：向量自动管理内存，无需手动分配和释放。数组（特别是动态数组）需要程序员小心管理内存。
*   **功能丰富**：向量提供了许多内置方法（如 `size()`, `at()`, `begin()`, `end()`），而数组的功能相对基础。
*   **安全性**：向量的 `at()` 方法会进行边界检查，访问越界时会抛出异常，而数组的 `[]` 操作符不进行边界检查，可能导致未定义行为。

对于大多数情况，向量是比原始数组更安全、更便捷的选择。

---

## 总结 🎯

本节课中我们一起学习了向量的进阶操作。我们探讨了三种遍历向量的方法：基于范围的for循环、索引循环和迭代器循环，并了解了它们各自的优缺点。我们重点练习了如何使用迭代器在遍历过程中定位并安全地删除特定元素。最后，我们对比了向量与传统数组的主要区别，认识到向量在动态性和安全性方面的优势。

![](img/0b1fc2c8dbc4dd9e9c6cc85820740939_83.png)

掌握这些操作将使你能够更高效地使用向量这一强大的容器，为处理更复杂的数据结构问题做好准备。