# C++ for Java Programmers: Lecture 6: 内存模型、多维数组与参数传递

在本节课中，我们将深入探讨C++的内存模型，理解指针和数组在内存中的布局，并学习如何向函数传递各种类型的参数，包括数组和多维数组。掌握这些概念对于编写高效、正确的C++程序至关重要。

## 内存模型与编译过程

上一节我们回顾了指针和引用的基本用法。本节中，我们来看看代码在计算机内部是如何被组织和执行的。

当我们编译代码时，编译器会经历多个阶段：
1.  **预处理器**：处理`#include`等指令，展开头文件，移除注释。
2.  **编译器**：将代码转换为汇编语言。
3.  **汇编器**：将汇编代码转换为机器码（0和1）。

编译器会维护一个**符号表**，用于记录变量名与其内存地址的对应关系。编译完成后，机器码中只使用内存地址，变量名不再存在。

![](img/46ee6a334ee9cfefc04f18b2ccac6ec9_1.png)

程序运行时，操作系统会为它分配一个虚拟内存空间。这个空间主要分为以下几个区域：
*   **代码区**：存放编译后的机器指令。
*   **数据区**：存放全局变量和静态局部变量。
*   **栈**：存放函数的局部变量。函数调用时，其局部变量被压入栈；函数返回时，这些变量被弹出。栈从高地址向低地址增长。
*   **堆**：用于动态内存分配（如使用`new`或`malloc`）。堆从低地址向高地址增长。程序员需要手动管理堆内存的分配和释放。

## 指针、引用与内存模型

![](img/46ee6a334ee9cfefc04f18b2ccac6ec9_3.png)

让我们通过代码示例，将变量、指针和引用映射到内存模型中。

![](img/46ee6a334ee9cfefc04f18b2ccac6ec9_5.png)

![](img/46ee6a334ee9cfefc04f18b2ccac6ec9_7.png)

```cpp
int x = 3;
int y = 5;
int* p = &x; // p 是一个指向 x 的指针
```

![](img/46ee6a334ee9cfefc04f18b2ccac6ec9_9.png)

在内存中，`x`、`y`和`p`作为局部变量，会被分配在栈上。假设它们的地址如下（为简化，使用短地址表示）：
*   `x` 存储在地址 `0xF130`，值为 `3`。
*   `y` 存储在地址 `0xF134`，值为 `5`。
*   `p` 存储在地址 `0xF138`，其**存储的值**是 `x` 的地址 `0xF130`。

![](img/46ee6a334ee9cfefc04f18b2ccac6ec9_11.png)

![](img/46ee6a334ee9cfefc04f18b2ccac6ec9_13.png)

因此，指针 `p` 本身有一个存储位置（`0xF138`），其内容指向另一个内存位置（`0xF130`）。通过解引用操作 `*p`，我们可以访问或修改 `x` 的值。

![](img/46ee6a334ee9cfefc04f18b2ccac6ec9_15.png)

引用则可以看作是一个变量的别名。它必须在创建时初始化，且之后不能更改其绑定的对象。

![](img/46ee6a334ee9cfefc04f18b2ccac6ec9_17.png)

```cpp
int& r = x; // r 是 x 的引用（别名）
```

在编译器内部，引用可能通过指针机制实现，也可能直接在符号表中处理为别名。对于程序员而言，`r` 和 `x` 访问的是同一块内存。

![](img/46ee6a334ee9cfefc04f18b2ccac6ec9_19.png)

![](img/46ee6a334ee9cfefc04f18b2ccac6ec9_20.png)

![](img/46ee6a334ee9cfefc04f18b2ccac6ec9_22.png)

## 数组与内存模型

![](img/46ee6a334ee9cfefc04f18b2ccac6ec9_24.png)

数组在内存中是连续存储的。声明一个数组时，数组名本质上是一个指向数组首元素的**常量指针**。

![](img/46ee6a334ee9cfefc04f18b2ccac6ec9_26.png)

```cpp
int a[5] = {0, 1, 2, 3, 4};
int* pa = a; // pa 是一个指向数组 a 的指针
```

![](img/46ee6a334ee9cfefc04f18b2ccac6ec9_28.png)

在内存中，数组 `a` 的五个元素 `0, 1, 2, 3, 4` 会连续存放。数组名 `a` 的值就是第一个元素 `a[0]` 的地址。下标操作 `a[i]` 在内部被转换为 `*(a + i)`，即“从首地址向后移动 `i` 个元素大小的距离，然后取该地址的值”。

动态分配的数组则存储在堆上：

![](img/46ee6a334ee9cfefc04f18b2ccac6ec9_30.png)

```cpp
int* da = new int[3] {5, 6, 7}; // da 指向堆上的数组
// ... 使用 da
delete[] da; // 必须手动释放内存
```

![](img/46ee6a334ee9cfefc04f18b2ccac6ec9_32.png)

这里，指针变量 `da` 本身在栈上，但它存储的值是堆上数组的起始地址。

## 字符数组（C风格字符串）

![](img/46ee6a334ee9cfefc04f18b2ccac6ec9_34.png)

C风格字符串是以空字符 `\0` 结尾的字符数组。许多字符串处理函数都依赖这个终止符来判断字符串的结束。

![](img/46ee6a334ee9cfefc04f18b2ccac6ec9_36.png)

```cpp
char c1[] = {'C', 'S', '3', '6', '8'}; // 错误：缺少 \0，打印可能导致越界
char c2[] = {'C', 'S', '3', '6', '8', '\0'}; // 正确
char c3[] = "CS368"; // 正确：编译器自动添加 \0
```

忘记空终止符是常见的错误来源。在现代C++中，建议使用 `std::string` 类型来避免这些问题。

## 多维数组

多维数组在内存中也是线性连续存储的。例如，一个 `3行 x 4列` 的二维数组：

```cpp
int md[3][4] = {
    {11, 12, 13, 14},
    {21, 22, 23, 24},
    {31, 32, 33, 34}
};
```

在内存中的布局顺序是：`11, 12, 13, 14, 21, 22, 23, 24, 31, 32, 33, 34`。`md[1]` 表示第二行的首地址，其类型是 `int*`。

![](img/46ee6a334ee9cfefc04f18b2ccac6ec9_38.png)

可以使用嵌套的范围for循环来遍历多维数组（C++11）：

![](img/46ee6a334ee9cfefc04f18b2ccac6ec9_40.png)

```cpp
for (auto& row : md) { // row 是对一个“包含4个int的数组”的引用
    for (int& elem : row) {
        cout << elem << ' ';
    }
    cout << endl;
}
```

![](img/46ee6a334ee9cfefc04f18b2ccac6ec9_42.png)

![](img/46ee6a334ee9cfefc04f18b2ccac6ec9_44.png)

## 参数传递

向函数传递参数主要有以下几种方式：

**1. 按值传递**
这是默认方式。函数获得实参的一个副本，对副本的修改不影响原始数据。

```cpp
void dontChangeX(int x) {
    x = 5; // 只修改了局部副本
}
int main() {
    int x = 3;
    dontChangeX(x); // x 仍然是 3
}
```

![](img/46ee6a334ee9cfefc04f18b2ccac6ec9_46.png)

**2. 按引用传递**
函数参数是实参的引用（别名）。对形参的修改直接影响实参。常用于避免复制大型对象，或需要函数修改外部变量时。

![](img/46ee6a334ee9cfefc04f18b2ccac6ec9_48.png)

![](img/46ee6a334ee9cfefc04f18b2ccac6ec9_49.png)

```cpp
void callByReference(int& x) {
    x = 5; // 直接修改了 main 中的 x
}
int main() {
    int x = 3;
    callByReference(x); // x 变为 5
}
```

如果函数不会修改参数，应使用 `const` 引用，如 `void func(const BigObject& obj)`。

**3. 按指针传递**
与按引用传递类似，但语法上需要显式使用地址操作符 `&` 和解引用操作符 `*`。这种方式明确地向调用者暗示参数可能被修改。

```cpp
void callByPointer(int* xPtr) {
    *xPtr = 7; // 解引用并修改
}
int main() {
    int x = 3;
    callByPointer(&x); // 传递 x 的地址，x 变为 7
}
```

**4. 传递数组**
当数组作为函数参数时，实际上传递的是指向其首元素的指针。因此，函数内部无法直接获知数组的大小，通常需要额外传递一个大小参数。

```cpp
void printArray(int arr[], int size) { // `int arr[]` 等价于 `int* arr`
    for (int i = 0; i < size; ++i) {
        cout << arr[i] << ' ';
    }
}
```

由于传递的是指针，函数内对数组元素的修改会影响原始数组。

**5. 传递多维数组**
传递多维数组时，必须指定除第一维之外的所有维度大小。

```cpp
void printMatrix(int matrix[][4], int rows) { // 必须指定列数 4
    for (int i = 0; i < rows; ++i) {
        for (int j = 0; j < 4; ++j) {
            cout << matrix[i][j] << ' ';
        }
        cout << endl;
    }
}
// 也可以写成：void printMatrix(int (*matrix)[4], int rows)
```

## 返回指针或引用

函数可以返回指针或引用，但必须格外小心，**绝不能返回指向局部变量（位于栈上）的指针或引用**，因为函数返回后局部变量就被销毁了。

```cpp
// 错误示例：返回局部变量的引用
int& badFunction() {
    int localVar = 42;
    return localVar; // 危险！localVar 即将被销毁
}

// 正确示例：返回动态分配内存的指针（调用者负责 delete）
int* createArray(int size) {
    int* arr = new int[size];
    // ... 初始化 arr
    return arr; // 返回堆上内存的地址
}
// 调用者必须：int* myArr = createArray(10); ... delete[] myArr;

// 正确示例：返回传入参数的引用
const int& findMax(const std::vector<int>& vec) {
    int maxIndex = 0;
    // ... 查找最大值的索引
    return vec[maxIndex]; // 返回 vec 中某个元素的引用，安全
}
```

## 总结

![](img/46ee6a334ee9cfefc04f18b2ccac6ec9_51.png)

本节课中我们一起学习了C++程序的内存布局，理解了栈、堆、代码区、数据区的概念。我们深入探讨了指针和数组在内存中的表示，以及它们之间的紧密联系。我们还学习了如何向函数传递各种类型的参数，包括基本类型、数组、多维数组，并比较了按值传递、按引用传递和按指针传递的区别与适用场景。最后，我们了解了在函数中返回指针或引用时需要避免的陷阱。掌握这些底层知识，将帮助你写出更高效、更健壮的C++代码。