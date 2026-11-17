# 023：非变异算法 part1 🧮

在本节课中，我们将继续学习C++标准模板库中的非变异算法。我们将首先了解如何在迭代器范围内搜索最大或最小元素，接着探讨著名的`for_each`算法，它用于访问范围内的每个元素并对其执行操作。最后，我们将学习`equal`和`mismatch`算法，它们用于检查两个范围是否相等，并在不相等时找出第一个不匹配的位置。

## 查找最大与最小元素 🔍

![](img/8014d5f1512346ad32cbe277c91c93a0_1.png)

![](img/8014d5f1512346ad32cbe277c91c93a0_2.png)

![](img/8014d5f1512346ad32cbe277c91c93a0_3.png)

![](img/8014d5f1512346ad32cbe277c91c93a0_4.png)

![](img/8014d5f1512346ad32cbe277c91c93a0_5.png)

![](img/8014d5f1512346ad32cbe277c91c93a0_6.png)

上一节我们介绍了查找算法，本节中我们来看看如何在一个范围内查找最大或最小的元素。STL提供了`max_element`和`min_element`算法来完成这项任务。

![](img/8014d5f1512346ad32cbe277c91c93a0_8.png)

![](img/8014d5f1512346ad32cbe277c91c93a0_10.png)

这些算法接受前向迭代器，因为它们需要保存找到的最大或最小值的迭代器位置。默认情况下，它们使用`operator<`进行比较，但你也可以传入一个自定义的二元谓词来定义比较逻辑。

![](img/8014d5f1512346ad32cbe277c91c93a0_12.png)

以下是这些算法的函数签名：

![](img/8014d5f1512346ad32cbe277c91c93a0_14.png)

![](img/8014d5f1512346ad32cbe277c91c93a0_15.png)


![](img/8014d5f1512346ad32cbe277c91c93a0_17.png)


![](img/8014d5f1512346ad32cbe277c91c93a0_19.png)

![](img/8014d5f1512346ad32cbe277c91c93a0_20.png)

![](img/8014d5f1512346ad32cbe277c91c93a0_21.png)

![](img/8014d5f1512346ad32cbe277c91c93a0_23.png)


![](img/8014d5f1512346ad32cbe277c91c93a0_25.png)

![](img/8014d5f1512346ad32cbe277c91c93a0_26.png)

```cpp
template< class ForwardIt >
ForwardIt max_element( ForwardIt first, ForwardIt last );
template< class ForwardIt, class Compare >
ForwardIt max_element( ForwardIt first, ForwardIt last, Compare comp );
template< class ForwardIt >
ForwardIt min_element( ForwardIt first, ForwardIt last );
template< class ForwardIt, class Compare >
ForwardIt min_element( ForwardIt first, ForwardIt last, Compare comp );
```

值得注意的是，与`find_if`或`count_if`等算法不同，`max_element`和`min_element`的谓词版本没有`_if`后缀，这有时会让人感到困惑。

![](img/8014d5f1512346ad32cbe277c91c93a0_28.png)

![](img/8014d5f1512346ad32cbe277c91c93a0_29.png)

![](img/8014d5f1512346ad32cbe277c91c93a0_30.png)

![](img/8014d5f1512346ad32cbe277c91c93a0_31.png)

### 示例：查找最大奇数

![](img/8014d5f1512346ad32cbe277c91c93a0_33.png)

![](img/8014d5f1512346ad32cbe277c91c93a0_34.png)

为了演示如何使用自定义谓词，我们定义了一个函数对象（仿函数）来查找最大的奇数。

![](img/8014d5f1512346ad32cbe277c91c93a0_36.png)

![](img/8014d5f1512346ad32cbe277c91c93a0_37.png)

![](img/8014d5f1512346ad32cbe277c91c93a0_39.png)

```cpp
struct MaxOdd {
    bool operator()(int current_max, int value) const {
        return (value % 2 != 0) && (value > current_max);
    }
};
```

![](img/8014d5f1512346ad32cbe277c91c93a0_41.png)

![](img/8014d5f1512346ad32cbe277c91c93a0_42.png)

这个谓词检查一个数是否为奇数，并且是否大于当前的最大值。只有当两个条件都满足时，它才返回`true`，指示算法更新当前最大值。

![](img/8014d5f1512346ad32cbe277c91c93a0_44.png)

![](img/8014d5f1512346ad32cbe277c91c93a0_45.png)

![](img/8014d5f1512346ad32cbe277c91c93a0_47.png)

![](img/8014d5f1512346ad32cbe277c91c93a0_49.png)

以下是使用这些算法的完整示例步骤：

![](img/8014d5f1512346ad32cbe277c91c93a0_51.png)

![](img/8014d5f1512346ad32cbe277c91c93a0_52.png)

![](img/8014d5f1512346ad32cbe277c91c93a0_53.png)

![](img/8014d5f1512346ad32cbe277c91c93a0_55.png)

1.  使用默认比较查找最大和最小元素。
2.  使用`MaxOdd`仿函数查找最大奇数。
3.  使用一个泛型Lambda表达式查找最小奇数。

![](img/8014d5f1512346ad32cbe277c91c93a0_57.png)

![](img/8014d5f1512346ad32cbe277c91c93a0_58.png)

![](img/8014d5f1512346ad32cbe277c91c93a0_60.png)


![](img/8014d5f1512346ad32cbe277c91c93a0_61.png)

```cpp
#include <iostream>
#include <vector>
#include <algorithm>
int main() {
    std::vector<int> stats = {10, 25, -40, 30, 67, 9, 50};

    // 查找最大值
    auto max_it = std::max_element(stats.begin(), stats.end());
    if (max_it != stats.end()) {
        std::cout << "Max: " << *max_it << std::endl;
    }

    // 查找最小值
    auto min_it = std::min_element(stats.begin(), stats.end());
    if (min_it != stats.end()) {
        std::cout << "Min: " << *min_it << std::endl;
    }

    // 使用自定义谓词查找最大奇数
    auto max_odd_it = std::max_element(stats.begin(), stats.end(), MaxOdd());
    if (max_odd_it != stats.end()) {
        std::cout << "Max odd: " << *max_odd_it << std::endl;
    }

    // 使用Lambda查找最小奇数
    auto min_odd_it = std::min_element(stats.begin(), stats.end(),
        [](int x, int current_min) {
            return (x % 2 != 0) && (x < current_min);
        });
    if (min_odd_it != stats.end()) {
        std::cout << "Min odd: " << *min_odd_it << std::endl;
    }

    return 0;
}
```

![](img/8014d5f1512346ad32cbe277c91c93a0_63.png)

![](img/8014d5f1512346ad32cbe277c91c93a0_64.png)

![](img/8014d5f1512346ad32cbe277c91c93a0_66.png)

**一个重要注意事项**：如果自定义谓词的条件（例如“是奇数”）在整个范围内都不满足，算法将返回范围内的第一个元素作为结果。这是因为算法内部首先将结果初始化为第一个元素，然后遍历后续元素，仅在谓词返回`true`时才更新结果。因此，在设计谓词时需要考虑到这种边界情况。

![](img/8014d5f1512346ad32cbe277c91c93a0_68.png)

## for_each 算法 🔄

![](img/8014d5f1512346ad32cbe277c91c93a0_70.png)

![](img/8014d5f1512346ad32cbe277c91c93a0_71.png)

![](img/8014d5f1512346ad32cbe277c91c93a0_72.png)

![](img/8014d5f1512346ad32cbe277c91c93a0_73.png)

了解了如何查找极值后，我们来看一个用于处理范围内每个元素的算法：`for_each`。这个算法会对给定范围内的每个元素应用一个指定的函数。

![](img/8014d5f1512346ad32cbe277c91c93a0_75.png)

`for_each`的函数签名如下：

![](img/8014d5f1512346ad32cbe277c91c93a0_77.png)

![](img/8014d5f1512346ad32cbe277c91c93a0_78.png)

![](img/8014d5f1512346ad32cbe277c91c93a0_79.png)

![](img/8014d5f1512346ad32cbe277c91c93a0_81.png)

```cpp
template< class InputIt, class UnaryFunction >
UnaryFunction for_each( InputIt first, InputIt last, UnaryFunction f );
```

![](img/8014d5f1512346ad32cbe277c91c93a0_83.png)

算法遍历从`first`到`last`（不包括`last`）的每个元素，并对每个元素调用一元函数`f`。它最终会返回这个函数对象，这允许我们获取函数在调用过程中可能累积的状态。

![](img/8014d5f1512346ad32cbe277c91c93a0_85.png)

![](img/8014d5f1512346ad32cbe277c91c93a0_86.png)

### 示例：打印并计数

我们创建一个`Print`仿函数，它会在每次被调用时打印元素值并增加一个内部计数器。

![](img/8014d5f1512346ad32cbe277c91c93a0_88.png)

![](img/8014d5f1512346ad32cbe277c91c93a0_89.png)

![](img/8014d5f1512346ad32cbe277c91c93a0_90.png)

![](img/8014d5f1512346ad32cbe277c91c93a0_91.png)

```cpp
struct Print {
    std::ostream& os;
    int count = 0;

    Print(std::ostream& os) : os(os) {}

    template<typename T>
    void operator()(const T& x) {
        ++count;
        os << x << ' ';
    }

    int getCount() const { return count; }
};
```

![](img/8014d5f1512346ad32cbe277c91c93a0_92.png)

![](img/8014d5f1512346ad32cbe277c91c93a0_94.png)

![](img/8014d5f1512346ad32cbe277c91c93a0_96.png)

在主程序中，我们使用`for_each`算法：


![](img/8014d5f1512346ad32cbe277c91c93a0_98.png)

![](img/8014d5f1512346ad32cbe277c91c93a0_99.png)

![](img/8014d5f1512346ad32cbe277c91c93a0_100.png)

```cpp
#include <iostream>
#include <algorithm>
int main() {
    int arr[] = {5, 2, 8, 1, 9};
    int* end = arr + sizeof(arr)/sizeof(arr[0]);

    Print printer(std::cout);
    printer = std::for_each(arr, end, printer);

    std::cout << "\nPrinted " << printer.getCount() << " elements." << std::endl;
    return 0;
}
```

在这个例子中，`for_each`遍历数组，对每个元素调用`printer`的`operator()`，从而打印元素并计数。最后，我们通过返回的仿函数获取打印的总次数。

![](img/8014d5f1512346ad32cbe277c91c93a0_102.png)

![](img/8014d5f1512346ad32cbe277c91c93a0_103.png)

![](img/8014d5f1512346ad32cbe277c91c93a0_104.png)

![](img/8014d5f1512346ad32cbe277c91c93a0_105.png)

![](img/8014d5f1512346ad32cbe277c91c93a0_106.png)

![](img/8014d5f1512346ad32cbe277c91c93a0_107.png)

![](img/8014d5f1512346ad32cbe277c91c93a0_108.png)

![](img/8014d5f1512346ad32cbe277c91c93a0_109.png)

**与现代C++的对比**：在C++11引入基于范围的for循环之后，`for_each`的使用频率有所下降。基于范围的for循环语法更简洁。此外，`for_each`无法提前退出循环（除非抛出异常），因此在需要灵活控制循环流程时，传统的for循环或基于范围的for循环可能更合适。

## 比较算法：equal 与 mismatch ⚖️

![](img/8014d5f1512346ad32cbe277c91c93a0_111.png)

![](img/8014d5f1512346ad32cbe277c91c93a0_112.png)

![](img/8014d5f1512346ad32cbe277c91c93a0_113.png)

![](img/8014d5f1512346ad32cbe277c91c93a0_114.png)

![](img/8014d5f1512346ad32cbe277c91c93a0_116.png)

最后，我们学习两个用于比较范围的算法：`equal`和`mismatch`。`equal`检查两个范围是否完全相等，而`mismatch`则找出两个范围中第一个不匹配的元素位置。

![](img/8014d5f1512346ad32cbe277c91c93a0_118.png)

### equal 算法

![](img/8014d5f1512346ad32cbe277c91c93a0_120.png)

![](img/8014d5f1512346ad32cbe277c91c93a0_121.png)

![](img/8014d5f1512346ad32cbe277c91c93a0_122.png)

![](img/8014d5f1512346ad32cbe277c91c93a0_123.png)

`equal`算法检查第一个范围是否与第二个范围相等。它也可以接受一个二元谓词来自定义“相等”的比较方式。

![](img/8014d5f1512346ad32cbe277c91c93a0_125.png)

![](img/8014d5f1512346ad32cbe277c91c93a0_126.png)


![](img/8014d5f1512346ad32cbe277c91c93a0_128.png)

![](img/8014d5f1512346ad32cbe277c91c93a0_129.png)

![](img/8014d5f1512346ad32cbe277c91c93a0_131.png)

![](img/8014d5f1512346ad32cbe277c91c93a0_133.png)

![](img/8014d5f1512346ad32cbe277c91c93a0_135.png)

```cpp
template< class InputIt1, class InputIt2 >
bool equal( InputIt1 first1, InputIt1 last1, InputIt2 first2 );
template< class InputIt1, class InputIt2, class BinaryPredicate >
bool equal( InputIt1 first1, InputIt1 last1, InputIt2 first2, BinaryPredicate p );
```

![](img/8014d5f1512346ad32cbe277c91c93a0_137.png)

![](img/8014d5f1512346ad32cbe277c91c93a0_138.png)

**重要**：`equal`只接受第二个范围的起始迭代器`first2`。它假设第二个范围至少与第一个范围一样长。因此，在调用`equal`之前，确保第二个范围有足够的长度是程序员的责任，否则会导致未定义行为。

### mismatch 算法

![](img/8014d5f1512346ad32cbe277c91c93a0_140.png)

![](img/8014d5f1512346ad32cbe277c91c93a0_141.png)

![](img/8014d5f1512346ad32cbe277c91c93a0_142.png)

![](img/8014d5f1512346ad32cbe277c91c93a0_143.png)

![](img/8014d5f1512346ad32cbe277c91c93a0_144.png)

![](img/8014d5f1512346ad32cbe277c91c93a0_145.png)

![](img/8014d5f1512346ad32cbe277c91c93a0_146.png)

![](img/8014d5f1512346ad32cbe277c91c93a0_147.png)

`mismatch`算法比较两个范围，并返回一个`std::pair`，其中包含指向两个范围中第一个不匹配元素的迭代器。

![](img/8014d5f1512346ad32cbe277c91c93a0_149.png)


![](img/8014d5f1512346ad32cbe277c91c93a0_151.png)

```cpp
template< class InputIt1, class InputIt2 >
std::pair<InputIt1, InputIt2> mismatch( InputIt1 first1, InputIt1 last1, InputIt2 first2 );
template< class InputIt1, class InputIt2, class BinaryPredicate >
std::pair<InputIt1, InputIt2> mismatch( InputIt1 first1, InputIt1 last1, InputIt2 first2, BinaryPredicate p );
```

![](img/8014d5f1512346ad32cbe277c91c93a0_153.png)

![](img/8014d5f1512346ad32cbe277c91c93a0_154.png)

![](img/8014d5f1512346ad32cbe277c91c93a0_155.png)

![](img/8014d5f1512346ad32cbe277c91c93a0_156.png)

![](img/8014d5f1512346ad32cbe277c91c93a0_158.png)

### 示例：查找不匹配项

![](img/8014d5f1512346ad32cbe277c91c93a0_160.png)

以下示例演示了如何使用`equal`和`mismatch`，并引入了`std::distance`算法来计算迭代器之间的距离。

![](img/8014d5f1512346ad32cbe277c91c93a0_162.png)

![](img/8014d5f1512346ad32cbe277c91c93a0_163.png)

![](img/8014d5f1512346ad32cbe277c91c93a0_165.png)


![](img/8014d5f1512346ad32cbe277c91c93a0_167.png)

![](img/8014d5f1512346ad32cbe277c91c93a0_168.png)

![](img/8014d5f1512346ad32cbe277c91c93a0_169.png)

![](img/8014d5f1512346ad32cbe277c91c93a0_171.png)

```cpp
#include <iostream>
#include <vector>
#include <algorithm>
#include <iterator> // for std::distance
template<typename InputIt1, typename InputIt2>
void find_mismatches(InputIt1 first1, InputIt1 last1, InputIt2 first2, InputIt2 last2) {
    // 首先检查两个范围长度是否相同
    if (std::distance(first1, last1) != std::distance(first2, last2)) {
        std::cout << "Ranges have different sizes.\n";
        return;
    }

    // 使用 equal 检查整体是否相等
    if (std::equal(first1, last1, first2)) {
        std::cout << "Ranges are equal.\n";
    } else {
        std::cout << "Ranges are not equal.\n";
        // 使用 mismatch 找到第一个不匹配点
        auto mismatch_pair = std::mismatch(first1, last1, first2);
        if (mismatch_pair.first != last1) {
            std::cout << "First mismatch at: "
                      << *mismatch_pair.first << " vs " << *mismatch_pair.second << std::endl;
        }
        // 可以继续从下一个位置开始寻找更多不匹配
        // 例如：auto next_mismatch = std::mismatch(std::next(mismatch_pair.first), last1, std::next(mismatch_pair.second));
    }
}

int main() {
    std::vector<int> v1 = {10, 20, 30, 40, 50};
    std::vector<int> v2 = v1; // 拷贝，相等
    int arr[] = {10, 40, 60, 80, 100}; // 不相等

    std::cout << "Comparing v1 and v2 (should be equal):\n";
    find_mismatches(v1.begin(), v1.end(), v2.begin(), v2.end());

    std::cout << "\nComparing v1 and arr (should have mismatches):\n";
    find_mismatches(v1.begin(), v1.end(), std::begin(arr), std::end(arr));

    return 0;
}
```

![](img/8014d5f1512346ad32cbe277c91c93a0_173.png)

![](img/8014d5f1512346ad32cbe277c91c93a0_174.png)

![](img/8014d5f1512346ad32cbe277c91c93a0_175.png)

![](img/8014d5f1512346ad32cbe277c91c93a0_176.png)

![](img/8014d5f1512346ad32cbe277c91c93a0_177.png)

在这个例子中，第一次比较（两个相同的`vector`）会输出“Ranges are equal.”。第二次比较（`vector`和数组）会输出“Ranges are not equal.”，并指出第一个不匹配的元素是20和40。

![](img/8014d5f1512346ad32cbe277c91c93a0_179.png)

## 总结 📚

![](img/8014d5f1512346ad32cbe277c91c93a0_181.png)

![](img/8014d5f1512346ad32cbe277c91c93a0_182.png)

![](img/8014d5f1512346ad32cbe277c91c93a0_183.png)

本节课中我们一起学习了C++ STL中的几个关键非变异算法：
*   **`max_element` / `min_element`**：用于在范围内查找最大或最小元素，支持自定义比较谓词。
*   **`for_each`**：对范围内的每个元素应用一个函数，虽然仍有用武之地，但在许多场景下已被基于范围的for循环所取代。
*   **`equal`**：检查两个范围是否完全相等。
*   **`mismatch`**：找出两个范围中第一个不匹配的位置。

我们还了解了使用这些算法时的一些注意事项，例如自定义谓词在`max_element/min_element`中的边界情况，以及确保传递给`equal`的第二个范围足够长。掌握这些算法将帮助你更高效地处理和比较容器中的数据。