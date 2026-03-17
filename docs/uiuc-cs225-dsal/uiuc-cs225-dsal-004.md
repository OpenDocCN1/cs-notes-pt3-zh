# 数据结构与算法：第4讲：参数传递与内存管理 🧠

![](img/96def365bcdb88c79d8cca26a613f02e_1.png)

![](img/96def365bcdb88c79d8cca26a613f02e_3.png)

![](img/96def365bcdb88c79d8cca26a613f02e_5.png)

![](img/96def365bcdb88c79d8cca26a613f02e_7.png)

在本节课中，我们将学习C++中参数传递的三种主要方式：按值传递、按指针传递和按引用传递。我们还将探讨动态内存分配（堆内存）的基本概念，包括如何使用`new`和`delete`来管理数组。

![](img/96def365bcdb88c79d8cca26a613f02e_9.png)

---

![](img/96def365bcdb88c79d8cca26a613f02e_11.png)

![](img/96def365bcdb88c79d8cca26a613f02e_13.png)

![](img/96def365bcdb88c79d8cca26a613f02e_14.png)

![](img/96def365bcdb88c79d8cca26a613f02e_16.png)

## 概述

![](img/96def365bcdb88c79d8cca26a613f02e_18.png)

![](img/96def365bcdb88c79d8cca26a613f02e_20.png)

我们将从回顾堆内存分配开始，特别是动态数组的创建与销毁。接着，我们会深入探讨函数调用时参数传递的三种不同方式，分析它们的工作原理、性能差异以及适用场景。

![](img/96def365bcdb88c79d8cca26a613f02e_22.png)

![](img/96def365bcdb88c79d8cca26a613f02e_24.png)

![](img/96def365bcdb88c79d8cca26a613f02e_26.png)

---

![](img/96def365bcdb88c79d8cca26a613f02e_28.png)

## 堆内存与动态数组 🧱

![](img/96def365bcdb88c79d8cca26a613f02e_30.png)

![](img/96def365bcdb88c79d8cca26a613f02e_31.png)

![](img/96def365bcdb88c79d8cca26a613f02e_33.png)

![](img/96def365bcdb88c79d8cca26a613f02e_35.png)

上一节我们介绍了堆内存的基本概念。本节中，我们来看看如何使用`new`和`delete`操作符来创建和销毁动态数组。

![](img/96def365bcdb88c79d8cca26a613f02e_37.png)

![](img/96def365bcdb88c79d8cca26a613f02e_39.png)

在C++中，使用`new`关键字配合方括号可以创建动态数组。例如：

![](img/96def365bcdb88c79d8cca26a613f02e_41.png)

![](img/96def365bcdb88c79d8cca26a613f02e_42.png)

![](img/96def365bcdb88c79d8cca26a613f02e_44.png)

```cpp
int size = 10;
int* x = new int[size];
```

![](img/96def365bcdb88c79d8cca26a613f02e_46.png)

![](img/96def365bcdb88c79d8cca26a613f02e_48.png)

这行代码的含义是：在堆上分配足够存储`size`个整数的内存，并将这块内存的起始地址赋值给指针`x`。数组的大小在**运行时**确定，因此它是“动态”的。

动态数组在内存中的存储方式如下图所示。指针`x`存储的是数组第一个元素的地址。

![](img/96def365bcdb88c79d8cca26a613f02e_50.png)

![](img/96def365bcdb88c79d8cca26a613f02e_52.png)

```
内存布局示例：
x -> [int0][int1][int2]...[int(size-1)]
```

当使用完动态数组后，必须使用`delete[]`来释放内存：

![](img/96def365bcdb88c79d8cca26a613f02e_54.png)

![](img/96def365bcdb88c79d8cca26a613f02e_55.png)

![](img/96def365bcdb88c79d8cca26a613f02e_56.png)

```cpp
delete[] x;
```

![](img/96def365bcdb88c79d8cca26a613f02e_58.png)

![](img/96def365bcdb88c79d8cca26a613f02e_60.png)

使用`delete[]`（带方括号）而不是`delete`至关重要。`delete[]`会为数组中的**每一个元素**调用析构函数，然后释放整块内存。如果错误地使用`delete`（不带方括号），则只会释放内存而不会调用每个元素的析构函数，这可能导致资源泄漏（例如，如果数组元素是持有文件句柄或网络连接的对象）。

![](img/96def365bcdb88c79d8cca26a613f02e_62.png)

![](img/96def365bcdb88c79d8cca26a613f02e_63.png)

以下是关于动态数组的几个关键点：
*   动态数组的大小在程序运行时决定。
*   数组变量（如`x`）本身是一个指针，它存储数组首元素的地址。
*   使用`x[i]`访问元素时，编译器会计算从起始地址偏移`i`个元素后的位置。
*   每个`new[]`操作都必须有一个对应的`delete[]`操作，以正确释放内存。

![](img/96def365bcdb88c79d8cca26a613f02e_65.png)

---

![](img/96def365bcdb88c79d8cca26a613f02e_67.png)

![](img/96def365bcdb88c79d8cca26a613f02e_69.png)

## 函数参数传递方式 🔄

![](img/96def365bcdb88c79d8cca26a613f02e_71.png)

理解了内存的基本操作后，我们来看看如何将数据传递给函数。C++提供了三种主要的参数传递方式，它们各有特点。

![](img/96def365bcdb88c79d8cca26a613f02e_73.png)

![](img/96def365bcdb88c79d8cca26a613f02e_75.png)

![](img/96def365bcdb88c79d8cca26a613f02e_76.png)

### 按值传递 📥

![](img/96def365bcdb88c79d8cca26a613f02e_78.png)

按值传递是默认的方式。当调用函数时，实参的值会被**复制**一份，传递给函数的形参。函数内部对形参的任何修改都不会影响原始的实参。

![](img/96def365bcdb88c79d8cca26a613f02e_80.png)

![](img/96def365bcdb88c79d8cca26a613f02e_82.png)

考虑一个合并两个立方体（`Cube`对象）的函数：

![](img/96def365bcdb88c79d8cca26a613f02e_84.png)

![](img/96def365bcdb88c79d8cca26a613f02e_86.png)

```cpp
Cube joinCubes(Cube c1, Cube c2) {
    int totalVol = c1.getVolume() + c2.getVolume();
    double newLength = cbrt(totalVol);
    Cube result(newLength);
    return result;
}

![](img/96def365bcdb88c79d8cca26a613f02e_88.png)

![](img/96def365bcdb88c79d8cca26a613f02e_89.png)

![](img/96def365bcdb88c79d8cca26a613f02e_91.png)

![](img/96def365bcdb88c79d8cca26a613f02e_93.png)

![](img/96def365bcdb88c79d8cca26a613f02e_95.png)

// 调用
Cube* c1 = new Cube(4);
Cube* c2 = new Cube(5);
Cube c3 = joinCubes(*c1, *c2); // 注意：传递的是解引用后的对象
```

![](img/96def365bcdb88c79d8cca26a613f02e_97.png)

在这个例子中：
1.  `*c1`和`*c2`（即`Cube`对象）被完整地复制到函数`joinCubes`的局部变量`c1`和`c2`中。
2.  函数内部创建了一个新的`Cube`对象`result`。
3.  函数返回时，`result`被复制给外部的`c3`。

![](img/96def365bcdb88c79d8cca26a613f02e_99.png)

![](img/96def365bcdb88c79d8cca26a613f02e_100.png)

![](img/96def365bcdb88c79d8cca26a613f02e_102.png)

这个过程可能创建多个临时副本，如果`Cube`对象很大（例如包含大量数据），复制开销会很高。它的优点是安全，因为函数无法修改原始的`c1`和`c2`对象。

![](img/96def365bcdb88c79d8cca26a613f02e_104.png)

### 按指针传递 🎯

![](img/96def365bcdb88c79d8cca26a613f02e_106.png)

![](img/96def365bcdb88c79d8cca26a613f02e_108.png)

![](img/96def365bcdb88c79d8cca26a613f02e_110.png)

按指针传递时，传递的是实参的**内存地址**。函数接收一个指针（地址的副本），通过这个指针可以访问和修改原始数据。

![](img/96def365bcdb88c79d8cca26a613f02e_112.png)

![](img/96def365bcdb88c79d8cca26a613f02e_114.png)

![](img/96def365bcdb88c79d8cca26a613f02e_116.png)

以下是使用指针的`joinCubes`版本：

![](img/96def365bcdb88c79d8cca26a613f02e_118.png)

![](img/96def365bcdb88c79d8cca26a613f02e_120.png)

![](img/96def365bcdb88c79d8cca26a613f02e_121.png)

```cpp
Cube joinCubes(Cube* c1, Cube* c2) {
    int totalVol = c1->getVolume() + c2->getVolume(); // 使用 -> 操作符
    double newLength = cbrt(totalVol);
    Cube result(newLength);
    return result;
}

![](img/96def365bcdb88c79d8cca26a613f02e_123.png)

![](img/96def365bcdb88c79d8cca26a613f02e_124.png)

![](img/96def365bcdb88c79d8cca26a613f02e_126.png)

![](img/96def365bcdb88c79d8cca26a613f02e_128.png)

// 调用
Cube* c1 = new Cube(4);
Cube* c2 = new Cube(5);
Cube c3 = joinCubes(c1, c2); // 直接传递指针
```

在这个例子中：
*   传递给函数的是指针`c1`和`c2`的**值**（即地址），而不是整个`Cube`对象。复制一个地址的成本很低。
*   函数内部通过指针（使用`->`操作符）直接操作堆上的原始`Cube`对象。
*   这避免了复制大对象的开销，效率更高。

![](img/96def365bcdb88c79d8cca26a613f02e_130.png)

![](img/96def365bcdb88c79d8cca26a613f02e_132.png)

**但是**，按指针传递存在风险：函数可以通过指针修改调用者不希望被修改的数据。此外，指针可能为`nullptr`，需要在函数内进行检查。

![](img/96def365bcdb88c79d8cca26a613f02e_134.png)

### 按引用传递 🔗

![](img/96def365bcdb88c79d8cca26a613f02e_136.png)

![](img/96def365bcdb88c79d8cca26a613f02e_138.png)

![](img/96def365bcdb88c79d8cca26a613f02e_140.png)

![](img/96def365bcdb88c79d8cca26a613f02e_142.png)

![](img/96def365bcdb88c79d8cca26a613f02e_144.png)

按引用传递在语法上像按值传递一样简洁，但在效果上类似于按指针传递（直接操作原始数据）。引用是变量的一个“别名”。

![](img/96def365bcdb88c79d8cca26a613f02e_146.png)

以下是使用引用的`joinCubes`版本：

![](img/96def365bcdb88c79d8cca26a613f02e_148.png)

![](img/96def365bcdb88c79d8cca26a613f02e_150.png)

![](img/96def365bcdb88c79d8cca26a613f02e_151.png)

```cpp
Cube joinCubes(Cube& c1, Cube& c2) { // 参数类型是 Cube&
    int totalVol = c1.getVolume() + c2.getVolume(); // 使用 . 操作符
    double newLength = cbrt(totalVol);
    Cube result(newLength);
    return result;
}

![](img/96def365bcdb88c79d8cca26a613f02e_153.png)

![](img/96def365bcdb88c79d8cca26a613f02e_154.png)

// 调用
Cube* c1 = new Cube(4);
Cube* c2 = new Cube(5);
Cube c3 = joinCubes(*c1, *c2); // 传递解引用后的对象，但函数接收的是引用
```

![](img/96def365bcdb88c79d8cca26a613f02e_156.png)

在这个例子中：
*   函数签名中的`Cube&`表示参数是引用。
*   调用时，`c1`和`c2`成为外部`Cube`对象的别名。函数内对`c1`、`c2`的操作直接作用于原始的堆对象。
*   它兼具了按指针传递的效率（无对象复制）和按值传递的语法简洁性（使用`.`操作符）。

![](img/96def365bcdb88c79d8cca26a613f02e_158.png)

![](img/96def365bcdb88c79d8cca26a613f02e_159.png)

![](img/96def365bcdb88c79d8cca26a613f02e_160.png)

![](img/96def365bcdb88c79d8cca26a613f02e_161.png)

![](img/96def365bcdb88c79d8cca26a613f02e_163.png)

![](img/96def365bcdb88c79d8cca26a613f02e_165.png)

引用必须在创建时初始化，且一旦绑定到一个对象就不能再指向其他对象，这比指针更安全一些，但函数仍然能够修改原始数据。

![](img/96def365bcdb88c79d8cca26a613f02e_167.png)

![](img/96def365bcdb88c79d8cca26a613f02e_169.png)

![](img/96def365bcdb88c79d8cca26a613f02e_171.png)

![](img/96def365bcdb88c79d8cca26a613f02e_173.png)

---

![](img/96def365bcdb88c79d8cca26a613f02e_174.png)

![](img/96def365bcdb88c79d8cca26a613f02e_176.png)

## 三种传递方式的对比 📊

为了更清晰地理解，我们来总结一下三种参数传递方式的关键区别：

![](img/96def365bcdb88c79d8cca26a613f02e_178.png)

![](img/96def365bcdb88c79d8cca26a613f02e_180.png)

| 特性 | 按值传递 | 按指针传递 | 按引用传递 |
| :--- | :--- | :--- | :--- |
| **传递的内容** | 对象的完整副本 | 对象地址的副本 | 对象的别名（通常由编译器实现为指针） |
| **函数内修改** | **不影响**原始对象 | **会影响**原始对象 | **会影响**原始对象 |
| **空值有效性** | 总是有效（是副本） | 可能为`nullptr` | 总是有效（必须绑定到对象） |
| **语法** | `func(Cube c)` | `func(Cube* c)` | `func(Cube& c)` |
| **访问成员** | `c.getVolume()` | `c->getVolume()` | `c.getVolume()` |
| **性能** | 可能较慢（复制开销） | 快（只复制地址） | 快（通常等同于指针） |
| **安全性** | 高（隔离性好） | 中低（可能误修改或空指针） | 中（可修改原始数据，但无空引用） |

![](img/96def365bcdb88c79d8cca26a613f02e_182.png)

**如何选择？**
*   当需要保护原始数据不被修改，且对象很小或复制成本可接受时，使用**按值传递**。
*   当需要高效传递大型对象、数据结构，或者需要能够接收空值（`nullptr`）时，使用**按指针传递**。
*   当需要高效传递大型对象、数据结构，且语法简洁性很重要，同时确定实参一定有效时，使用**按引用传递**。

![](img/96def365bcdb88c79d8cca26a613f02e_184.png)

在实际C++编程中，为了同时获得**高效性**和**安全性**（防止意外修改），常常会使用**常量引用**（`const Cube&`），这将是下一讲的重要内容。

![](img/96def365bcdb88c79d8cca26a613f02e_186.png)

---

![](img/96def365bcdb88c79d8cca26a613f02e_188.png)

![](img/96def365bcdb88c79d8cca26a613f02e_190.png)

## 总结

本节课中我们一起学习了：
1.  **动态数组管理**：使用`new[]`在堆上分配数组，并使用`delete[]`正确释放，确保调用所有元素的析构函数。
2.  **参数传递的三种方式**：
    *   **按值传递**：安全但可能有复制开销。传递副本。
    *   **按指针传递**：高效灵活，可直接修改原始数据或处理空指针，但不够安全。传递地址。
    *   **按引用传递**：高效且语法简洁，直接操作原始数据，但不能为空。传递别名。

![](img/96def365bcdb88c79d8cca26a613f02e_192.png)

![](img/96def365bcdb88c79d8cca26a613f02e_194.png)

![](img/96def365bcdb88c79d8cca26a613f02e_196.png)

理解这些内存管理和参数传递的基础，对于编写高效、正确的C++程序至关重要，尤其是在实现复杂的数据结构与算法时。