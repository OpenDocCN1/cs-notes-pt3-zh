# 学习编程：基础知识：1.3：循环遍历索引 🔄

![](img/cb17adcb4d26ea65543b9ecadd9087e0_0.png)

![](img/cb17adcb4d26ea65543b9ecadd9087e0_2.png)

在本节课中，我们将学习如何使用 `for` 循环来遍历字符串和列表的**索引**，而不是直接遍历它们的元素。这将使我们能够解决一些仅靠遍历元素无法解决的问题。

![](img/cb17adcb4d26ea65543b9ecadd9087e0_4.png)

![](img/cb17adcb4d26ea65543b9ecadd9087e0_5.png)

## 为什么需要遍历索引？ 🤔

在前面的课程中，我们使用 `for` 循环来遍历字符串的字符以及列表的项。然而，有些问题需要我们比较一个元素与其相邻元素，或者需要知道元素在序列中的具体位置。这时，直接访问元素的索引就变得至关重要。

例如，我们需要比较字符串中相邻的字符是否相同。仅仅知道字符本身是不够的，我们还需要知道每个字符在字符串中的位置，才能找到它“旁边”的字符进行比较。

## 问题一：统计相邻重复字符对 📊

我们的第一个任务是编写一个函数，统计一个字符串中相邻且相同的字符对的数量。

![](img/cb17adcb4d26ea65543b9ecadd9087e0_7.png)

例如，在字符串 `"ACCFGG"` 中，有三对相邻的相同字符：`CC`、`GG` 和 `FF`。

![](img/cb17adcb4d26ea65543b9ecadd9087e0_9.png)

### 解决思路

要解决这个问题，我们需要比较字符串中每一对相邻的字符。这意味着我们需要访问字符的索引。

*   索引 `0` 的字符需要与索引 `1` 的字符比较。
*   索引 `1` 的字符需要与索引 `2` 的字符比较。
*   以此类推，直到比较索引 `-2`（倒数第二个）和索引 `-1`（最后一个）的字符。

![](img/cb17adcb4d26ea65543b9ecadd9087e0_11.png)

我们可以用公式来描述这个过程：比较字符串在索引 `i` 和索引 `i+1` 处的字符。

![](img/cb17adcb4d26ea65543b9ecadd9087e0_13.png)

为了生成这些 `i` 值，我们将使用 `range` 函数。我们需要 `i` 的值从 `0` 开始，一直到字符串长度减 `2`（即倒数第二个索引）。因此，循环可以这样写：

```python
for i in range(len(s) - 1):
    # s[i] 将与 s[i+1] 比较
```

![](img/cb17adcb4d26ea65543b9ecadd9087e0_15.png)

### 编写函数

![](img/cb17adcb4d26ea65543b9ecadd9087e0_17.png)

以下是实现该功能的函数 `count_adjacent_repeats`：

![](img/cb17adcb4d26ea65543b9ecadd9087e0_19.png)

![](img/cb17adcb4d26ea65543b9ecadd9087e0_21.png)

```python
def count_adjacent_repeats(s):
    """
    返回字符串 s 中相邻重复字符对的数量。
    """
    repeats = 0  # 初始化计数器
    for i in range(len(s) - 1):  # 遍历到倒数第二个字符的索引
        if s[i] == s[i + 1]:     # 比较当前字符和下一个字符
            repeats = repeats + 1 # 如果相同，计数器加1
    return repeats                # 返回最终计数
```

![](img/cb17adcb4d26ea65543b9ecadd9087e0_23.png)

![](img/cb17adcb4d26ea65543b9ecadd9087e0_25.png)

让我们测试一下这个函数：

![](img/cb17adcb4d26ea65543b9ecadd9087e0_27.png)

![](img/cb17adcb4d26ea65543b9ecadd9087e0_28.png)

```python
print(count_adjacent_repeats("ACCFGG"))  # 输出：3
print(count_adjacent_repeats("ABCCBBA")) # 输出：2
```

![](img/cb17adcb4d26ea65543b9ecadd9087e0_30.png)

函数按预期工作。通过遍历索引，我们成功地比较了每一对相邻的字符。

![](img/cb17adcb4d26ea65543b9ecadd9087e0_32.png)

## 问题二：列表左移 🔀

![](img/cb17adcb4d26ea65543b9ecadd9087e0_34.png)

现在，我们来看另一个需要遍历索引的问题：编写一个函数，将列表中的所有元素向左移动一位，并将第一个元素移到列表末尾。

![](img/cb17adcb4d26ea65543b9ecadd9087e0_36.png)

![](img/cb17adcb4d26ea65543b9ecadd9087e0_37.png)

函数的前提条件是列表长度至少为 `1`。

![](img/cb17adcb4d26ea65543b9ecadd9087e0_39.png)

例如，列表 `["A", "B", "C", "D"]` 经过左移后，应该变成 `["B", "C", "D", "A"]`。

### 解决思路

这个操作的关键在于，当我们把第二个元素（索引 `1`）移动到第一个位置（索引 `0`）时，会覆盖掉原来的第一个元素。因此，我们需要在移动开始前，用一个变量（例如 `first_item`）保存第一个元素的值。

然后，我们从索引 `1` 开始遍历到列表末尾。在循环中，我们将每个元素赋值给它左边的位置：`L[i-1] = L[i]`。

循环结束后，所有元素都向左移动了一位，最后一个位置是空的。这时，我们将之前保存的 `first_item` 赋值给最后一个位置 `L[-1]`。

### 编写函数

以下是实现该功能的函数 `shift_left`：

```python
def shift_left(L):
    """
    将列表 L 中的元素向左移动一位。
    第一个元素被移动到列表末尾。
    修改原列表，不返回新列表。
    """
    if len(L) > 0:  # 确保列表非空
        first_item = L[0]  # 保存第一个元素
        for i in range(1, len(L)):  # 从索引1开始遍历
            L[i - 1] = L[i]         # 将当前元素移到左边
        L[-1] = first_item          # 将原第一个元素放到末尾
```

让我们测试一下这个函数：

![](img/cb17adcb4d26ea65543b9ecadd9087e0_41.png)

```python
letters = ["A", "B", "C", "D"]
shift_left(letters)
print(letters)  # 输出：['B', 'C', 'D', 'A']
```

![](img/cb17adcb4d26ea65543b9ecadd9087e0_43.png)

函数成功修改了原列表。注意，这个函数没有返回值（或者说返回 `None`），它的作用是通过修改参数来体现的。

![](img/cb17adcb4d26ea65543b9ecadd9087e0_45.png)

## 总结 📝

![](img/cb17adcb4d26ea65543b9ecadd9087e0_47.png)

在本节课中，我们一起学习了如何使用 `for` 循环和 `range()` 函数来遍历序列的索引，而不仅仅是元素值。

![](img/cb17adcb4d26ea65543b9ecadd9087e0_49.png)

![](img/cb17adcb4d26ea65543b9ecadd9087e0_50.png)

*   **核心概念**：当我们需要根据元素在序列中的**位置**来解决问题时（例如比较相邻项、交换位置），遍历索引是必要的方法。
*   **关键工具**：`range(len(sequence))` 是生成索引的常用模式。通过调整 `range` 的起始和结束参数，我们可以精确控制需要遍历哪些位置。
*   **应用实例**：
    1.  我们编写了 `count_adjacent_repeats` 函数，通过比较 `s[i]` 和 `s[i+1]` 来统计相邻重复字符。
    2.  我们编写了 `shift_left` 函数，通过操作 `L[i-1] = L[i]` 来实现列表元素的左移，并在过程中使用临时变量保存关键数据。

![](img/cb17adcb4d26ea65543b9ecadd9087e0_52.png)

![](img/cb17adcb4d26ea65543b9ecadd9087e0_54.png)

掌握遍历索引的技巧，极大地扩展了我们处理序列数据的能力，为解决更复杂的编程问题奠定了基础。