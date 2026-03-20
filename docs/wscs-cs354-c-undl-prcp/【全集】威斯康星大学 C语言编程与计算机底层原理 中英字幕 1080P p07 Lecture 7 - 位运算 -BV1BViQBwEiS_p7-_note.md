# C语言编程与计算机底层原理：第7讲：位运算 🧮

![](img/feddeade64179ad0e66ecd303c94c392_0.png)

![](img/feddeade64179ad0e66ecd303c94c392_2.png)

![](img/feddeade64179ad0e66ecd303c94c392_3.png)

![](img/feddeade64179ad0e66ecd303c94c392_4.png)

![](img/feddeade64179ad0e66ecd303c94c392_5.png)

![](img/feddeade64179ad0e66ecd303c94c392_6.png)

![](img/feddeade64179ad0e66ecd303c94c392_7.png)

![](img/feddeade64179ad0e66ecd303c94c392_8.png)

在本节课中，我们将要学习C语言中的位运算。位运算允许我们直接操作数据的二进制位，这对于理解计算机底层工作原理、编写高效代码以及处理特定任务（如图形数据）至关重要。我们将介绍六种主要的位运算符，并通过实例展示其应用。

![](img/feddeade64179ad0e66ecd303c94c392_10.png)

![](img/feddeade64179ad0e66ecd303c94c392_11.png)

![](img/feddeade64179ad0e66ecd303c94c392_12.png)

![](img/feddeade64179ad0e66ecd303c94c392_13.png)

![](img/feddeade64179ad0e66ecd303c94c392_14.png)

## 概述

位运算是对二进制位进行的数学操作。它让我们得以一窥CPU指令集的能力，并学习如何利用这些知识来提升代码的运行速度。我们将探讨位掩码、打包整数和位标志等核心概念。

![](img/feddeade64179ad0e66ecd303c94c392_16.png)

![](img/feddeade64179ad0e66ecd303c94c392_17.png)

![](img/feddeade64179ad0e66ecd303c94c392_18.png)

![](img/feddeade64179ad0e66ecd303c94c392_19.png)

![](img/feddeade64179ad0e66ecd303c94c392_20.png)

![](img/feddeade64179ad0e66ecd303c94c392_21.png)

![](img/feddeade64179ad0e66ecd303c94c392_22.png)

## 位运算符介绍

![](img/feddeade64179ad0e66ecd303c94c392_24.png)

![](img/feddeade64179ad0e66ecd303c94c392_25.png)

![](img/feddeade64179ad0e66ecd303c94c392_26.png)

![](img/feddeade64179ad0e66ecd303c94c392_28.png)

C语言提供了六种位运算符，用于直接操作整数中的二进制位。

![](img/feddeade64179ad0e66ecd303c94c392_30.png)

![](img/feddeade64179ad0e66ecd303c94c392_32.png)

以下是这些运算符的列表：
*   **按位或 (OR)**：运算符为 `|`。
*   **按位与 (AND)**：运算符为 `&`。
*   **按位取反 (NOT)**：运算符为 `~`。
*   **按位异或 (XOR)**：运算符为 `^`。
*   **左移 (Left Shift)**：运算符为 `<<`。
*   **右移 (Right Shift)**：运算符为 `>>`。

## 运算符详解与示例

![](img/feddeade64179ad0e66ecd303c94c392_34.png)

![](img/feddeade64179ad0e66ecd303c94c392_35.png)

![](img/feddeade64179ad0e66ecd303c94c392_36.png)

![](img/feddeade64179ad0e66ecd303c94c392_37.png)

上一节我们列出了所有位运算符，本节中我们来看看它们具体是如何工作的。理解它们的最佳方式是通过具体的二进制示例。

![](img/feddeade64179ad0e66ecd303c94c392_39.png)

![](img/feddeade64179ad0e66ecd303c94c392_40.png)

![](img/feddeade64179ad0e66ecd303c94c392_41.png)

### 按位或 (|)

![](img/feddeade64179ad0e66ecd303c94c392_43.png)

按位或运算符对两个操作数的每一位进行比较。如果**任意一个**对应位为1，则结果位为1；只有两个位都为0时，结果位才为0。

![](img/feddeade64179ad0e66ecd303c94c392_45.png)

![](img/feddeade64179ad0e66ecd303c94c392_47.png)

![](img/feddeade64179ad0e66ecd303c94c392_48.png)

**示例**：
假设 `x = 1010` (十进制10)， `y = 0110` (十进制6)。
```
x: 1 0 1 0
y: 0 1 1 0
-----------
x|y: 1 1 1 0  (十进制14)
```
在B0位（最右位），0|0=0；在B1位，1|1=1；在B2位，0|1=1；在B3位，1|0=1。

![](img/feddeade64179ad0e66ecd303c94c392_50.png)

![](img/feddeade64179ad0e66ecd303c94c392_51.png)

![](img/feddeade64179ad0e66ecd303c94c392_53.png)

### 按位与 (&)

按位与运算符同样对每一位进行操作。只有当**两个**对应位都为1时，结果位才为1，否则为0。

![](img/feddeade64179ad0e66ecd303c94c392_55.png)

![](img/feddeade64179ad0e66ecd303c94c392_56.png)

![](img/feddeade64179ad0e66ecd303c94c392_57.png)

![](img/feddeade64179ad0e66ecd303c94c392_58.png)

**示例**：
使用相同的 `x` 和 `y`。
```
x: 1 0 1 0
y: 0 1 1 0
-----------
x&y: 0 0 1 0  (十进制2)
```
在B0位，0&0=0；在B1位，1&1=1；在B2位，0&1=0；在B3位，1&0=0。

### 按位取反 (~)

![](img/feddeade64179ad0e66ecd303c94c392_60.png)

![](img/feddeade64179ad0e66ecd303c94c392_62.png)

按位取反是一元运算符，它对操作数的每一位执行逻辑“非”操作，即将1变为0，将0变为1。这相当于求二进制数的“反码”。

![](img/feddeade64179ad0e66ecd303c94c392_64.png)

**示例**：
对 `x = 1010` 取反。
```
x: 1 0 1 0
-----------
~x: 0 1 0 1  (十进制5)
```

![](img/feddeade64179ad0e66ecd303c94c392_66.png)

![](img/feddeade64179ad0e66ecd303c94c392_68.png)

### 按位异或 (^)

![](img/feddeade64179ad0e66ecd303c94c392_70.png)

![](img/feddeade64179ad0e66ecd303c94c392_71.png)

![](img/feddeade64179ad0e66ecd303c94c392_73.png)

按位异或运算符在对应位**不相同**时结果为1，相同时结果为0。

![](img/feddeade64179ad0e66ecd303c94c392_75.png)

![](img/feddeade64179ad0e66ecd303c94c392_76.png)

![](img/feddeade64179ad0e66ecd303c94c392_77.png)

![](img/feddeade64179ad0e66ecd303c94c392_78.png)

**示例**：
使用 `x` 和 `y`。
```
x: 1 0 1 0
y: 0 1 1 0
-----------
x^y: 1 1 0 0  (十进制12)
```
在B0位，0^0=0；在B1位，1^1=0；在B2位，0^1=1；在B3位，1^0=1。

![](img/feddeade64179ad0e66ecd303c94c392_80.png)

### 移位运算符 (<<, >>)

![](img/feddeade64179ad0e66ecd303c94c392_82.png)

![](img/feddeade64179ad0e66ecd303c94c392_84.png)

移位运算符将二进制位向左或向右移动指定的位数。

![](img/feddeade64179ad0e66ecd303c94c392_86.png)

![](img/feddeade64179ad0e66ecd303c94c392_87.png)

**左移 (<<)**：将所有位向左移动，右侧空出的位用0填充，左侧移出的位被丢弃。
**示例**：`1010 << 2` 结果为 `101000`。

![](img/feddeade64179ad0e66ecd303c94c392_89.png)

**右移 (>>)**：行为取决于操作数的类型。
*   对于**无符号**数，执行**逻辑右移**：左侧空出的位用0填充。
*   对于**有符号**数，通常执行**算术右移**：左侧空出的位用原数的符号位（最高位）填充。这可以保持负数的符号。

![](img/feddeade64179ad0e66ecd303c94c392_91.png)

**示例（算术右移）**：
假设有符号数 `x = 10011010`（负数）。
`x >> 2` 可能结果为 `11100110`，左侧移入了符号位1。

![](img/feddeade64179ad0e66ecd303c94c392_93.png)

![](img/feddeade64179ad0e66ecd303c94c392_94.png)

## 位运算的应用

![](img/feddeade64179ad0e66ecd303c94c392_96.png)

![](img/feddeade64179ad0e66ecd303c94c392_98.png)

理解了基本操作后，我们来看看位运算在实际编程中的强大用途。

![](img/feddeade64179ad0e66ecd303c94c392_100.png)

![](img/feddeade64179ad0e66ecd303c94c392_102.png)

### 位掩码

![](img/feddeade64179ad0e66ecd303c94c392_104.png)

![](img/feddeade64179ad0e66ecd303c94c392_105.png)

位掩码用于从数据中提取或设置特定的位。其核心思想是使用**按位与 (&)** 操作来“屏蔽”掉我们不关心的位。

![](img/feddeade64179ad0e66ecd303c94c392_107.png)

![](img/feddeade64179ad0e66ecd303c94c392_109.png)

![](img/feddeade64179ad0e66ecd303c94c392_110.png)

**示例：提取最低4位**
假设我们有一个8位数 `x = 10010010`，想得到它的最低4位 `0010`。
我们可以创建一个掩码 `00001111`（十进制15），然后进行按位与操作：
```
x:    1 0 0 1 0 0 1 0
掩码: 0 0 0 0 1 1 1 1
-----------------------
结果: 0 0 0 0 0 0 1 0
```
**代码实现**：`int low_bits = x & 0xF;` // 0xF 是十六进制，等于二进制 1111

![](img/feddeade64179ad0e66ecd303c94c392_112.png)

**示例：提取最高4位并移至低位**
要提取 `x = 10010010` 的最高4位 `1001` 并使其位于结果的低4位，需要两步：
1.  **右移**：`x >> 4` 得到 `00001001`。
2.  **掩码**：与 `00001111` 进行按位与（此例中可省略，因为高位已是0）。

![](img/feddeade64179ad0e66ecd303c94c392_113.png)

![](img/feddeade64179ad0e66ecd303c94c392_114.png)

![](img/feddeade64179ad0e66ecd303c94c392_115.png)

![](img/feddeade64179ad0e66ecd303c94c392_116.png)

![](img/feddeade64179ad0e66ecd303c94c392_117.png)

**代码实现**：`int high_bits = (x >> 4) & 0xF;`

![](img/feddeade64179ad0e66ecd303c94c392_119.png)

![](img/feddeade64179ad0e66ecd303c94c392_120.png)

![](img/feddeade64179ad0e66ecd303c94c392_121.png)

### 打包整数

![](img/feddeade64179ad0e66ecd303c94c392_123.png)

![](img/feddeade64179ad0e66ecd303c94c392_124.png)

在计算机图形学等领域，常需要将多个小整数（如颜色通道）打包到一个大整数中以节省空间。例如，将红(R)、绿(G)、蓝(B)、透明度(A)各1字节（0-255）打包成一个4字节（32位）整数。

![](img/feddeade64179ad0e66ecd303c94c392_126.png)

![](img/feddeade64179ad0e66ecd303c94c392_127.png)

**数据布局**：
```
位位置: 31-24    23-16    15-8     7-0
通道:     R        G        B        A
```

![](img/feddeade64179ad0e66ecd303c94c392_129.png)

![](img/feddeade64179ad0e66ecd303c94c392_130.png)

**示例：提取绿色通道(G)**
假设打包后的颜色值为 `0x00FF00FF`（绿色全满，其他为0）。绿色通道位于第16到23位。
1.  **右移**：将数值右移16位，使绿色通道移动到最低8位：`color >> 16`。
2.  **掩码**：与 `0xFF`（二进制`11111111`）进行按位与，确保只保留低8位。

![](img/feddeade64179ad0e66ecd303c94c392_131.png)

![](img/feddeade64179ad0e66ecd303c94c392_132.png)

![](img/feddeade64179ad0e66ecd303c94c392_133.png)

![](img/feddeade64179ad0e66ecd303c94c392_135.png)

![](img/feddeade64179ad0e66ecd303c94c392_136.png)

![](img/feddeade64179ad0e66ecd303c94c392_137.png)

**代码实现**：`int green = (packed_color >> 16) & 0xFF;`

![](img/feddeade64179ad0e66ecd303c94c392_139.png)

### 位标志（位域）

![](img/feddeade64179ad0e66ecd303c94c392_141.png)

![](img/feddeade64179ad0e66ecd303c94c392_142.png)

![](img/feddeade64179ad0e66ecd303c94c392_143.png)

![](img/feddeade64179ad0e66ecd303c94c392_144.png)

![](img/feddeade64179ad0e66ecd303c94c392_145.png)

![](img/feddeade64179ad0e66ecd303c94c392_146.png)

布尔值只需要1位存储，但C语言中一个`bool`或`int`会占用更多空间。位标志利用一个整数的不同位来存储多个布尔值，极大节省内存。

![](img/feddeade64179ad0e66ecd303c94c392_148.png)

![](img/feddeade64179ad0e66ecd303c94c392_150.png)

**步骤**：
1.  为每个标志定义唯一的位位置（掩码）。
    ```c
    #define FLAG_OLD      (1 << 0) // 0001
    #define FLAG_EMPLOYED (1 << 1) // 0010
    #define FLAG_PARENT   (1 << 2) // 0100
    ```
2.  使用**按位或 (|)** 来组合设置多个标志。
    ```c
    int person_status = FLAG_OLD | FLAG_EMPLOYED | FLAG_PARENT; // 二进制 0111
    ```
3.  使用**按位与 (&)** 来检查某个标志是否被设置。
    ```c
    if (person_status & FLAG_OLD) {
        // 这个人是“老”的，条件为真
    }
    if (!(person_status & FLAG_FERRARI)) {
        // 这个人没有法拉利，条件为真
    }
    ```

![](img/feddeade64179ad0e66ecd303c94c392_152.png)

![](img/feddeade64179ad0e66ecd303c94c392_153.png)

![](img/feddeade64179ad0e66ecd303c94c392_154.png)

![](img/feddeade64179ad0e66ecd303c94c392_155.png)

![](img/feddeade64179ad0e66ecd303c94c392_157.png)

![](img/feddeade64179ad0e66ecd303c94c392_158.png)

## 用于快速乘除的技巧

![](img/feddeade64179ad0e66ecd303c94c392_160.png)

![](img/feddeade64179ad0e66ecd303c94c392_161.png)

移位运算可以用于优化乘以或除以2的幂次方（如2、4、8、16）的操作，因为这在CPU上通常比直接乘除更快。

**原理**：
*   将一个数**左移 n 位**，相当于乘以 **2^n**。
    *   例如：`14 << 1` 等于 `28` (14*2)。`14 << 2` 等于 `56` (14*4)。
*   将一个数**右移 n 位**，相当于除以 **2^n**（对于非负整数是整除）。
    *   例如：`28 >> 1` 等于 `14` (28/2)。`28 >> 2` 等于 `7` (28/4)。

![](img/feddeade64179ad0e66ecd303c94c392_163.png)

**代码示例**：
```c
int multiplyBy8 = x << 3; // 等同于 x * 8
int divideBy4 = x >> 2;   // 等同于 x / 4 (x为非负整数时)
```
> **注意**：对于有符号负数，右移是算术右移，结果与除法略有不同（向负无穷取整，而C语言除法向零取整）。此技巧最安全地用于无符号数。

![](img/feddeade64179ad0e66ecd303c94c392_165.png)

![](img/feddeade64179ad0e66ecd303c94c392_166.png)

![](img/feddeade64179ad0e66ecd303c94c392_167.png)

![](img/feddeade64179ad0e66ecd303c94c392_168.png)

## 总结

![](img/feddeade64179ad0e66ecd303c94c392_170.png)

![](img/feddeade64179ad0e66ecd303c94c392_171.png)

本节课中我们一起学习了C语言的位运算。我们从六种基本的位运算符（`|`, `&`, `~`, `^`, `<<`, `>>`）开始，详细了解了它们的功能。接着，我们探讨了位运算的三个重要应用：使用**位掩码**提取和操作特定位；利用**打包整数**高效存储多个数据；以及通过**位标志**紧凑地存储布尔值集合。最后，我们学习了一个优化技巧：使用移位运算来加速乘以或除以2的幂次方的计算。掌握位运算能帮助你写出更高效、更接近机器底层的代码，并更好地理解数据在计算机中的表示形式。