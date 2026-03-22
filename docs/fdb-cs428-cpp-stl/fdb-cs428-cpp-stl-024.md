# 024：非变异算法 part2 🔍

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_1.png)

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_3.png)

在本节课中，我们将完成对C++标准模板库中非变异算法的学习，重点介绍用于在范围内进行搜索的算法。这些算法不会改变容器本身的内容，而是帮助我们查找特定的元素或序列。

上一节我们介绍了查找最大值、最小值等算法，本节中我们来看看如何在序列中进行更复杂的搜索。

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_5.png)

---

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_7.png)

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_9.png)

## 搜索算法概述

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_11.png)

STL提供了多种在序列中搜索元素的算法，主要包括：
*   **`search`**：在第一个范围中搜索第二个范围首次出现的位置，可以使用二元谓词或值进行比较。
*   **`search_n`**：在范围中搜索连续出现n次的某个值，同样可以使用二元谓词。
*   **`adjacent_find`**：在范围中搜索第一对相邻且相等的元素（或满足谓词条件的元素）。
*   **`binary_search`**：在已排序的范围内以对数时间复杂度查找某个元素。
*   **`lower_bound`**：与`binary_search`类似，但返回指向找到元素的迭代器，而不仅仅是布尔值。

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_13.png)

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_14.png)

---

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_15.png)

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_16.png)

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_17.png)

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_18.png)

## 使用 `search` 算法

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_20.png)

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_22.png)

`search` 算法用于在一个序列中查找另一个子序列首次出现的位置。

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_24.png)

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_25.png)

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_27.png)

以下是演示如何使用 `search` 算法的示例代码。我们定义了一个辅助函数 `search_for_subsequence`。

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_28.png)

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_30.png)

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_32.png)

```cpp
template <typename InputIterator1, typename InputIterator2>
void search_for_subsequence(InputIterator1 first1, InputIterator1 last1,
                            InputIterator2 first2, InputIterator2 last2) {
    auto it = std::search(first1, last1, first2, last2);
    if (it != last1) {
        std::cout << "子序列在索引 " << std::distance(first1, it) << " 处找到。\n";
    } else {
        std::cout << "未找到子序列。\n";
    }
}
```

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_34.png)

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_36.png)

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_38.png)

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_39.png)

在这个函数中：
1.  我们使用 `std::search(first1, last1, first2, last2)` 在范围 `[first1, last1)` 中搜索子序列 `[first2, last2)`。
2.  如果找到匹配，函数返回指向主序列中匹配起始位置的迭代器。
3.  我们使用 `std::distance` 计算该迭代器相对于序列起始点的距离，即索引位置。
4.  如果迭代器等于 `last1`，则表示未找到子序列。

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_41.png)

我们使用两个著名的句子进行测试：
*   主序列1（存储在 `vector<string>` 中）：`"now is the time for all good people to come to the aid of their party"`
*   主序列2（存储在 `list<string>` 中）：`"I've seen all good people turn their heads each day so satisfied I'm on my way"`
*   要搜索的子序列（存储在 `array<string, 3>` 中）：`"all good people"`

运行程序后，输出显示子序列在第一个向量的索引5处和第二个列表的索引2处被找到。这演示了如何编写通用的代码来搜索 `vector`、`list` 和 `array` 中的子序列。

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_43.png)

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_45.png)

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_47.png)

---

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_49.png)

## 使用 `search_n` 算法

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_50.png)

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_51.png)

`search_n` 算法用于在序列中查找连续出现 `n` 次的特定值。

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_53.png)

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_54.png)

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_55.png)

以下示例将展示如何使用 `search_n` 并配合自定义谓词进行更灵活的搜索。我们定义了一个辅助函数 `search_n_for_value`。

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_57.png)

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_59.png)

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_61.png)

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_63.png)

```cpp
template <typename ForwardIterator, typename Size, typename T, typename BinaryPredicate>
void search_n_for_value(ForwardIterator first, ForwardIterator last,
                        Size count, const T& value, BinaryPredicate pred) {
    auto it = first;
    while (it != last) {
        it = std::search_n(it, last, count, value, pred);
        if (it != last) {
            std::cout << "在索引 " << std::distance(first, it)
                      << " 处找到 " << count << " 个连续匹配值。\n";
            ++it; // 跳过当前匹配，继续搜索
        }
    }
    if (it == first) {
        std::cout << "未找到连续匹配值。\n";
    }
}
```

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_65.png)

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_66.png)

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_68.png)

在这个函数中：
1.  我们循环调用 `std::search_n`，每次从上次找到的位置之后开始搜索。
2.  谓词 `pred` 允许我们定义“匹配”的条件。在示例中，我们使用一个谓词来检查字符串的首字母是否等于给定的字符。
3.  每次找到匹配，就输出位置，然后递增迭代器以继续搜索剩余部分。

我们使用相同的两个句子进行测试，但这次搜索目标不同：
*   在第一个序列（向量）中，查找连续两个以字母 **‘T’** 开头的单词。
*   在第二个序列（列表）中，查找连续两个以字母 **‘S’** 开头的单词。

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_70.png)

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_71.png)

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_72.png)

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_73.png)

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_74.png)

程序输出显示，在第一个序列中，`"the"` 和 `"time"` 在索引2处匹配，`"to"` 和 `"the"` 在索引10处匹配。在第二个序列中，`"so"` 和 `"satisfied"` 被找到。这展示了 `search_n` 如何与自定义谓词结合，实现精细化的搜索。

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_75.png)

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_76.png)

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_78.png)

---

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_80.png)

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_81.png)

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_82.png)

## 使用 `adjacent_find` 算法

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_84.png)

`adjacent_find` 算法用于查找序列中第一对相邻且满足特定条件的元素。

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_85.png)

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_86.png)

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_88.png)

我们可以将其视为一个简化版的 `search_n`（其中 `n=2`）。以下示例演示了其用法。我们定义了一个辅助函数 `adjacent_find_for_pred`。

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_89.png)

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_90.png)

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_92.png)

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_94.png)

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_95.png)

```cpp
template <typename Container, typename BinaryPredicate>
void adjacent_find_for_pred(const Container& c, BinaryPredicate pred) {
    auto it = std::begin(c);
    while (it != std::end(c)) {
        it = std::adjacent_find(it, std::end(c), pred);
        if (it != std::end(c)) {
            std::cout << "在索引 " << std::distance(std::begin(c), it)
                      << " 处找到相邻匹配对。\n";
            ++it; // 跳过当前匹配，继续搜索
        }
    }
}
```

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_97.png)

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_98.png)

在这个函数中：
1.  逻辑与 `search_n_for_value` 类似，但调用的是 `std::adjacent_find`。
2.  它接受一个容器引用和一个二元谓词。谓词判断两个相邻元素是否“相等”（根据自定义条件）。
3.  在示例中，谓词检查两个字符串的首字母是否相同。

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_100.png)

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_101.png)

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_103.png)

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_105.png)

使用相同的测试数据，我们搜索相邻且首字母相同的单词对。输出结果与 `search_n` 示例类似，找到了 `"the"`/`"time"`、`"to"`/`"the"` 以及 `"so"`/`"satisfied"` 等配对。这展示了 STL 算法的通用性和强大之处，可以通过谓词实现非传统的、细粒度的匹配逻辑。

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_107.png)

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_109.png)

---

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_111.png)

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_112.png)

## 使用 `binary_search` 和 `lower_bound` 算法

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_114.png)

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_115.png)

`binary_search` 和 `lower_bound` 算法用于在**已排序**的序列中进行高效查找。

`binary_search` 只返回一个布尔值，表示元素是否存在。而 `lower_bound` 返回一个迭代器，指向第一个**不小于**给定值的元素，如果该元素等于给定值，则指向它。为了获得更实用的功能（即找到元素并获取其位置），我们可以基于 `lower_bound` 实现一个 `binary_find` 辅助函数。

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_117.png)

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_118.png)

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_119.png)

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_120.png)

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_121.png)

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_122.png)

首先，我们使用 `binary_search`：

```cpp
std::string search_words[] = {"find", "all", "good", "people"};
std::string quote[] = {"now", "is", "the", "time", "for", "all", "good", "people", "to", "come", "to", "the", "aid", "of", "their", "party"};

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_124.png)

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_125.png)

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_126.png)

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_127.png)

// 必须先排序
std::sort(std::begin(quote), std::end(quote));

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_129.png)

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_130.png)

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_131.png)

for (const auto& word : search_words) {
    if (std::binary_search(std::begin(quote), std::end(quote), word)) {
        std::cout << "找到单词: " << word << std::endl;
    } else {
        std::cout << "未找到单词: " << word << std::endl;
    }
}
```

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_132.png)

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_134.png)

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_135.png)

然后，我们实现并使用 `binary_find`：

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_137.png)

```cpp
template <typename ForwardIterator, typename T, typename Compare = std::less<>>
ForwardIterator binary_find(ForwardIterator first, ForwardIterator last, const T& value, Compare comp = {}) {
    first = std::lower_bound(first, last, value, comp);
    // 确保找到的元素确实等于 value，而不仅仅是“不小于”
    return (first != last && !comp(value, *first)) ? first : last;
}

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_139.png)

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_140.png)

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_141.png)

// 使用 binary_find
std::vector<std::string> sorted_vec(std::begin(quote), std::end(quote)); // 已排序的副本
for (const auto& word : search_words) {
    auto it = binary_find(sorted_vec.cbegin(), sorted_vec.cend(), word);
    if (it != sorted_vec.cend()) {
        std::cout << "单词 \"" << word << "\" 在索引 "
                  << std::distance(sorted_vec.cbegin(), it) << " 处找到。\n";
    }
}
```

在 `binary_find` 函数中：
1.  首先调用 `std::lower_bound` 在排序范围 `[first, last)` 中查找 `value`。
2.  检查返回的迭代器 `first` 是否有效（不等于 `last`）并且其指向的元素确实等于 `value`（通过 `!comp(value, *first)` 确保 `value` 不小于 `*first` 且 `*first` 也不小于 `value`）。
3.  如果条件满足，返回该迭代器；否则返回 `last` 表示未找到。

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_143.png)

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_144.png)

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_146.png)

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_148.png)

运行程序，`binary_search` 会告诉我们哪些单词存在。而 `binary_find` 不仅能确认存在，还能精确地给出每个找到的单词在已排序向量中的索引位置（例如，`"all"` 在索引1，`"good"` 在索引4）。这凸显了 `lower_bound` 在需要获取元素位置时比 `binary_search` 更有用。

---

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_150.png)

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_151.png)

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_152.png)

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_153.png)

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_154.png)

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_155.png)

## 总结 🎯

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_156.png)

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_157.png)

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_159.png)

本节课中我们一起学习了C++ STL中最后几个重要的非变异搜索算法：
1.  **`search`**：用于在序列中查找子序列。
2.  **`search_n`**：用于查找连续出现n次的元素。
3.  **`adjacent_find`**：用于查找相邻的匹配元素对。
4.  **`binary_search`** 与 **`lower_bound`**：用于在已排序序列中进行高效查找，其中 `lower_bound` 能提供元素位置信息，通常更实用。

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_161.png)

这些算法都支持通过自定义谓词（Predicate）来定义复杂的匹配规则，体现了STL的强大灵活性和通用性。它们都不会修改原始容器的内容。

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_162.png)

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_163.png)

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_164.png)

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_165.png)

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_166.png)

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_167.png)

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_169.png)

接下来，我们将开始讨论能够改变容器内容的**变异算法**。在进入正题之前，可能会先看一个有趣的案例研究，它综合运用了STL的多种特性（包括 `adjacent_find`），实现一个会议时间冲突检测工具，这将再次展示STL解决实际问题的能力。