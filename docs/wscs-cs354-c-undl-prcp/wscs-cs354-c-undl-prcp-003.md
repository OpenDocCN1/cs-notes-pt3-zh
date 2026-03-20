# 003：数组与指针的等价性 📚

![](img/88960f0f92259fe66d7c97d5819c0fe3_1.png)

在本节课中，我们将深入学习C语言中的数组和指针，探讨它们之间的紧密联系和关键区别。我们将通过实验来观察内存的分配方式，理解编译器如何处理这些数据结构，并学习如何安全有效地使用它们。

## 课程回顾与概述 🔄

![](img/88960f0f92259fe66d7c97d5819c0fe3_3.png)

上一节我们介绍了C语言的基础控制流和数据结构。本节中，我们将重点探讨指针和数组，特别是它们的等价性以及内存模型。

首先，我们快速回顾一下课程进度：
*   **控制流**：我们学习了 `if` 语句、`while`、`do-while`、`for` 循环以及基本的函数调用。
*   **数据结构**：我们介绍了基本数据类型（`char`, `int`, `float`, `double`）和一维数组。

![](img/88960f0f92259fe66d7c97d5819c0fe3_5.png)

今天，我们将深入探讨指针和数组，包括字符数组（字符串），并介绍多维数组的内存模型以及结构体（`struct`）的基本概念。

![](img/88960f0f92259fe66d7c97d5819c0fe3_7.png)

## 指针基础回顾 🧭

让我们从一个简单的指针示例开始，以巩固对指针的理解并连接内存模型。

我们创建两个整数和指向它们的指针，然后打印所有相关信息。

```c
#include <stdio.h>

int main() {
    int a = 3;
    int b = 4;

    int *pa = &a; // 指向a的指针
    int *pb = &b; // 指向b的指针

    // 打印变量a和b的值与地址
    printf("a contains %d at address %p\n", a, &a);
    printf("b contains %d at address %p\n", b, &b);

    // 打印指针的信息：解引用值、指针内容（地址）、指针自身的地址
    printf("*pa = %d, pa contains %p, address of pa is %p\n", *pa, pa, &pa);
    printf("*pb = %d, pb contains %p, address of pb is %p\n", *pb, pb, &pb);

    return 0;
}
```

运行此程序，输出类似于：
```
a contains 3 at address 0x0061FF1C
b contains 4 at address 0x0061FF18
*pa = 3, pa contains 0x0061FF1C, address of pa is 0x0061FF14
*pb = 4, pb contains 0x0061FF18, address of pb is 0x0061FF10
```

**内存模型分析**：
程序的内存被划分为几个部分：
1.  **代码区**：存储编译后的机器指令。
2.  **全局/静态区**：存储全局变量和字符串常量。
3.  **堆**：用于动态内存分配（后续课程讲解）。
4.  **栈**：用于函数调用、局部变量和参数。我们的变量 `a`, `b`, `pa`, `pb` 都存储在栈上。

栈从高地址向低地址增长。每个变量（`int` 或指针）在32位系统中占用4字节。指针变量存储的是它所指向变量的内存地址。`*` 操作符用于“解引用”，即跟随指针存储的地址去获取该地址处的值。

![](img/88960f0f92259fe66d7c97d5819c0fe3_9.png)

![](img/88960f0f92259fe66d7c97d5819c0fe3_10.png)

**编译器差异**：不同的编译器（如Windows的MinGW和Linux的GCC）可能以不同的顺序在栈上分配局部变量，但数组元素的地址通常是递增的。

![](img/88960f0f92259fe66d7c97d5819c0fe3_12.png)

![](img/88960f0f92259fe66d7c97d5819c0fe3_14.png)

## 数组与内存布局 🗂️

接下来，我们创建一个整数数组，并观察其在内存中的布局。

```c
#include <stdio.h>
#define ARRAY_MAX 5 // 使用编译器宏定义数组大小

![](img/88960f0f92259fe66d7c97d5819c0fe3_16.png)

![](img/88960f0f92259fe66d7c97d5819c0fe3_17.png)

![](img/88960f0f92259fe66d7c97d5819c0fe3_19.png)

int main() {
    int arr[ARRAY_MAX];
    for(int i = 0; i < ARRAY_MAX; i++) {
        arr[i] = i * 10; // 初始化数组
    }

    // 打印数组元素的值和地址
    for(int i = 0; i < ARRAY_MAX; i++) {
        printf("array[%d] = %d at address %p\n", i, arr[i], &arr[i]);
    }

    // 打印数组名本身
    printf("arr (array name) points to address %p\n", arr);
    printf("Address of arr (&arr) is also %p\n", &arr);

    return 0;
}
```

![](img/88960f0f92259fe66d7c97d5819c0fe3_21.png)

输出类似于：
```
array[0] = 0 at address 0x0061FEF4
array[1] = 10 at address 0x0061FEF8
array[2] = 20 at address 0x0061FEFC
array[3] = 30 at address 0x0061FF00
array[4] = 40 at address 0x0061FF04
arr (array name) points to address 0x0061FEF4
Address of arr (&arr) is also 0x0061FEF4
```

![](img/88960f0f92259fe66d7c97d5819c0fe3_23.png)

![](img/88960f0f92259fe66d7c97d5819c0fe3_25.png)

**关键发现**：
1.  数组元素在内存中是连续存储的，地址依次递增（每个`int`占4字节）。
2.  数组名 `arr` 本身**不是一个存储在某地址的独立指针变量**。它更像一个“常量指针”，其值就是数组第一个元素的地址 (`&arr[0]`)。因此，`arr` 和 `&arr` 的结果相同。
3.  C语言不进行数组边界检查。如果访问 `arr[5]`（越界），程序可能不会立即崩溃，但会读写未分配的内存，导致不可预知的行为（如覆盖其他变量），这是缓冲区溢出错误的基础。

![](img/88960f0f92259fe66d7c97d5819c0fe3_27.png)

![](img/88960f0f92259fe66d7c97d5819c0fe3_29.png)

![](img/88960f0f92259fe66d7c97d5819c0fe3_31.png)

## 指针与数组的等价性与差异 ⚖️

![](img/88960f0f92259fe66d7c97d5819c0fe3_33.png)

![](img/88960f0f92259fe66d7c97d5819c0fe3_35.png)

数组和指针在访问元素时语法可以互换，这是它们“等价性”的核心。但它们在声明和某些行为上有根本区别。

![](img/88960f0f92259fe66d7c97d5819c0fe3_37.png)

### 1. 使用指针访问数组
我们可以创建一个指针，让它指向数组，然后使用指针或数组下标来访问元素。

![](img/88960f0f92259fe66d7c97d5819c0fe3_39.png)

```c
int arr[5] = {0, 10, 20, 30, 40};
int *parr = arr; // parr 是指向数组的指针变量

![](img/88960f0f92259fe66d7c97d5819c0fe3_41.png)

![](img/88960f0f92259fe66d7c97d5819c0fe3_43.png)

![](img/88960f0f92259fe66d7c97d5819c0fe3_44.png)

![](img/88960f0f92259fe66d7c97d5819c0fe3_46.png)

![](img/88960f0f92259fe66d7c97d5819c0fe3_47.png)

![](img/88960f0f92259fe66d7c97d5819c0fe3_49.png)

// 以下三行输出相同的结果：0
printf("arr[0] = %d\n", arr[0]);
printf("*(arr + 0) = %d\n", *(arr + 0));
printf("*parr = %d\n", *parr);
printf("parr[0] = %d\n", parr[0]); // 指针也能用下标！

![](img/88960f0f92259fe66d7c97d5819c0fe3_51.png)

![](img/88960f0f92259fe66d7c97d5819c0fe3_53.png)

![](img/88960f0f92259fe66d7c97d5819c0fe3_55.png)

// 指针算术：编译器根据类型自动调整步长
parr = parr + 1; // parr 现在指向 arr[1]，地址增加了4字节(sizeof(int))
printf("After increment, *parr = %d (should be 10)\n", *parr);
```

**指针算术**：当对指针进行加/减运算时，编译器会根据指针指向的数据类型自动调整地址的偏移量。`parr + 1` 意味着 `parr的地址值 + 1 * sizeof(int)`。

![](img/88960f0f92259fe66d7c97d5819c0fe3_57.png)

![](img/88960f0f92259fe66d7c97d5819c0fe3_59.png)

![](img/88960f0f92259fe66d7c97d5819c0fe3_61.png)

![](img/88960f0f92259fe66d7c97d5819c0fe3_63.png)

![](img/88960f0f92259fe66d7c97d5819c0fe3_65.png)

![](img/88960f0f92259fe66d7c97d5819c0fe3_67.png)

![](img/88960f0f92259fe66d7c97d5819c0fe3_69.png)

### 2. 核心差异：可修改性
*   **指针是变量**：`parr` 本身存储在内存中（有地址 `&parr`），其存储的值（指向的地址）可以改变。
*   **数组名是常量**：`arr` 是标识符，不是变量。`arr = arr + 1;` 这样的赋值是**非法**的，编译器会报错。你不能改变 `arr` 代表的地址。

![](img/88960f0f92259fe66d7c97d5819c0fe3_71.png)

![](img/88960f0f92259fe66d7c97d5819c0fe3_73.png)

![](img/88960f0f92259fe66d7c97d5819c0fe3_75.png)

### 3. 数组下标访问的本质
表达式 `arr[i]` 在编译时会被转换为 `*(arr + i)`。这意味着：
*   `arr[i]` 等价于 `*(arr + i)`
*   `i[arr]` 这种奇怪的写法在语法上也是合法的，因为它等价于 `*(i + arr)`，但不建议使用。

![](img/88960f0f92259fe66d7c97d5819c0fe3_77.png)

## 数组作为函数参数 📤

![](img/88960f0f92259fe66d7c97d5819c0fe3_79.png)

![](img/88960f0f92259fe66d7c97d5819c0fe3_81.png)

![](img/88960f0f92259fe66d7c97d5819c0fe3_83.png)

在C语言中，所有参数都是“按值传递”。但当数组作为函数参数时，传递的实际上是数组首元素的地址（一个值），这模拟了“按引用传递”的效果。

```c
#include <stdio.h>
#define ARRAY_MAX 5

![](img/88960f0f92259fe66d7c97d5819c0fe3_85.png)

![](img/88960f0f92259fe66d7c97d5819c0fe3_87.png)

// 函数原型：参数可以写为 int arr[] 或 int *arr，它们是等价的。
void printArray(int arr[], int size); // size 需要额外传递，因为数组“退化”为指针

![](img/88960f0f92259fe66d7c97d5819c0fe3_89.png)

![](img/88960f0f92259fe66d7c97d5819c0fe3_91.png)

int main() {
    int myArr[ARRAY_MAX] = {1, 2, 3, 4, 5};
    printf("In main, address of myArr is %p\n", (void*)myArr);
    printArray(myArr, ARRAY_MAX);
    return 0;
}

![](img/88960f0f92259fe66d7c97d5819c0fe3_93.png)

// 函数定义
void printArray(int arr[], int size) { // 这里的arr实际上是一个指针
    printf("In printArray, parameter arr holds address %p\n", (void*)arr);
    for(int i = 0; i < size; i++) {
        printf("%d ", arr[i]); // 依然可以使用下标
    }
    printf("\n");
}
```

![](img/88960f0f92259fe66d7c97d5819c0fe3_95.png)

![](img/88960f0f92259fe66d7c97d5819c0fe3_97.png)

**重要**：
*   函数内的 `arr` 是一个独立的指针变量，它存储了主函数中 `myArr` 的地址。
*   通过这个指针，函数可以修改原始数组的内容。
*   函数无法通过 `sizeof(arr)` 获取原始数组的长度，因为 `arr` 已退化为指针。因此，通常需要额外传递数组大小参数。

![](img/88960f0f92259fe66d7c97d5819c0fe3_99.png)

![](img/88960f0f92259fe66d7c97d5819c0fe3_101.png)

![](img/88960f0f92259fe66d7c97d5819c0fe3_103.png)

![](img/88960f0f92259fe66d7c97d5819c0fe3_105.png)

## 字符数组与字符串 🔤

![](img/88960f0f92259fe66d7c97d5819c0fe3_107.png)

![](img/88960f0f92259fe66d7c97d5819c0fe3_109.png)

![](img/88960f0f92259fe66d7c97d5819c0fe3_111.png)

![](img/88960f0f92259fe66d7c97d5819c0fe3_113.png)

![](img/88960f0f92259fe66d7c97d5819c0fe3_115.png)

在C语言中，字符串本质上是字符数组，以空字符 `'\0'`（ASCII值为0）结尾。

```c
#include <stdio.h>

![](img/88960f0f92259fe66d7c97d5819c0fe3_117.png)

![](img/88960f0f92259fe66d7c97d5819c0fe3_119.png)

![](img/88960f0f92259fe66d7c97d5819c0fe3_121.png)

![](img/88960f0f92259fe66d7c97d5819c0fe3_123.png)

![](img/88960f0f92259fe66d7c97d5819c0fe3_125.png)

![](img/88960f0f92259fe66d7c97d5819c0fe3_127.png)

![](img/88960f0f92259fe66d7c97d5819c0fe3_129.png)

![](img/88960f0f92259fe66d7c97d5819c0fe3_131.png)

![](img/88960f0f92259fe66d7c97d5819c0fe3_133.png)

int main() {
    // 初始化字符串，编译器会自动添加 '\0'
    char str1[] = "Hello"; // 实际是 {'H','e','l','l','o','\0'}，占6字节
    char str2[10] = "World"; // 剩余字节初始化为0或垃圾值

    // 使用指针遍历字符串（直到遇到'\0'）
    char *p = str1;
    while(*p != '\0') {
        printf("%c ", *p);
        p++; // 指针移动到下一个字符
    }
    printf("\n");

    // 字符串复制示例（简化版，未考虑安全）
    char src[] = "Source";
    char dest[20];
    char *ps = src;
    char *pd = dest;
    while((*pd++ = *ps++) != '\0'); // 经典的字符串复制循环
    printf("Copied string: %s\n", dest);

    return 0;
}
```

![](img/88960f0f92259fe66d7c97d5819c0fe3_135.png)

![](img/88960f0f92259fe66d7c97d5819c0fe3_137.png)

![](img/88960f0f92259fe66d7c97d5819c0fe3_139.png)

**关键点**：
*   字符串字面量（如`"Hello"`）会自动包含终止符 `'\0'`。
*   许多标准库函数（如`strcpy`, `strlen`）都依赖这个终止符来工作。
*   确保字符数组有足够空间容纳字符串内容**和**终止符 `'\0'`，否则会导致缓冲区溢出。

## 总结 🎯

![](img/88960f0f92259fe66d7c97d5819c0fe3_141.png)

![](img/88960f0f92259fe66d7c97d5819c0fe3_143.png)

本节课我们一起深入学习了C语言中数组和指针的核心概念：
1.  **指针基础**：指针存储地址，`*` 用于解引用，`&` 用于取地址。
2.  **数组内存布局**：数组元素在内存中连续存储。数组名是一个指向首元素的常量指针。
3.  **指针与数组的等价性**：可以使用指针算术 `*(arr + i)` 来访问数组元素 `arr[i]`，反之亦然。
4.  **核心差异**：指针是变量，可修改其指向；数组名是常量，不可重新赋值。
5.  **函数参数**：传递数组时，实际传递的是其首地址，函数内通过指针操作原数组。
6.  **字符串**：C语言中的字符串是以 `'\0'` 结尾的字符数组，操作时需特别注意边界和终止符。

![](img/88960f0f92259fe66d7c97d5819c0fe3_145.png)

![](img/88960f0f92259fe66d7c97d5819c0fe3_147.png)

![](img/88960f0f92259fe66d7c97d5819c0fe3_149.png)

![](img/88960f0f92259fe66d7c97d5819c0fe3_151.png)

理解数组和指针的底层内存模型，是编写高效、安全C程序的关键，也是后续学习计算机体系结构和操作系统的基础。请务必动手实验代码，观察不同情况下的内存地址和行为。