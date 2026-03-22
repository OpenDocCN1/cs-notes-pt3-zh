# 020：功能适配器（第二部分）🚀

![](img/841b7f0aa929ea6656b076d5a9def536_1.png)

![](img/841b7f0aa929ea6656b076d5a9def536_2.png)

![](img/841b7f0aa929ea6656b076d5a9def536_3.png)

在本节课中，我们将继续学习C++标准模板库中的功能适配器。上一节我们介绍了绑定器，本节中我们来看看另一种功能适配器——否定器。我们将探讨几种不同的否定器，并通过示例展示其用法。同时，我们也会回顾绑定器，了解它们在不同C++标准版本中的演变。

![](img/841b7f0aa929ea6656b076d5a9def536_5.png)

![](img/841b7f0aa929ea6656b076d5a9def536_6.png)

![](img/841b7f0aa929ea6656b076d5a9def536_7.png)

![](img/841b7f0aa929ea6656b076d5a9def536_8.png)

![](img/841b7f0aa929ea6656b076d5a9def536_9.png)

![](img/841b7f0aa929ea6656b076d5a9def536_10.png)

![](img/841b7f0aa929ea6656b076d5a9def536_11.png)

## 否定器适配器概述

![](img/841b7f0aa929ea6656b076d5a9def536_13.png)

![](img/841b7f0aa929ea6656b076d5a9def536_14.png)

![](img/841b7f0aa929ea6656b076d5a9def536_16.png)

![](img/841b7f0aa929ea6656b076d5a9def536_17.png)

否定器适配器是一种函数对象，它可以封装另一个函数对象，并返回其结果的逻辑非。随着C++标准的发展，出现了几种不同的否定器。

![](img/841b7f0aa929ea6656b076d5a9def536_19.png)

![](img/841b7f0aa929ea6656b076d5a9def536_20.png)

![](img/841b7f0aa929ea6656b076d5a9def536_21.png)

以下是几种主要的否定器：
*   **`not1`**：用于处理一元函数或一元操作。
*   **`not2`**：用于处理二元函数或二元操作。
*   **`not_fn`**（或写作`not_function`）：一个较新的模板，可以同时处理一元或二元函数，无需像`not1`和`not2`那样在名称上区分。

![](img/841b7f0aa929ea6656b076d5a9def536_23.png)

![](img/841b7f0aa929ea6656b076d5a9def536_24.png)

![](img/841b7f0aa929ea6656b076d5a9def536_26.png)

![](img/841b7f0aa929ea6656b076d5a9def536_27.png)

## 示例一：使用否定器与算法

![](img/841b7f0aa929ea6656b076d5a9def536_29.png)

![](img/841b7f0aa929ea6656b076d5a9def536_30.png)

为了演示否定器的工作原理，我们首先创建一个简单的布尔函数对象模板，用于判断一个数字是否为奇数。

![](img/841b7f0aa929ea6656b076d5a9def536_32.png)

![](img/841b7f0aa929ea6656b076d5a9def536_34.png)

![](img/841b7f0aa929ea6656b076d5a9def536_35.png)

![](img/841b7f0aa929ea6656b076d5a9def536_36.png)

![](img/841b7f0aa929ea6656b076d5a9def536_38.png)

```cpp
template <typename T>
struct IsOdd {
    bool operator()(const T& number) const {
        return number % 2 != 0;
    }
};
```
这个`IsOdd`是一个一元函数对象，它接受一个类型为`T`的参数`number`，通过计算`number % 2`来判断是否为奇数（余数不为0则返回`true`）。

![](img/841b7f0aa929ea6656b076d5a9def536_40.png)

![](img/841b7f0aa929ea6656b076d5a9def536_42.png)

![](img/841b7f0aa929ea6656b076d5a9def536_43.png)

![](img/841b7f0aa929ea6656b076d5a9def536_44.png)

我们还将使用一个辅助函数`print_results`来输出计算结果，它利用了模板模板参数的技术。

![](img/841b7f0aa929ea6656b076d5a9def536_46.png)

![](img/841b7f0aa929ea6656b076d5a9def536_47.png)

![](img/841b7f0aa929ea6656b076d5a9def536_49.png)

![](img/841b7f0aa929ea6656b076d5a9def536_50.png)

### 使用 `remove_copy_if` 与 `not1`

首先，我们使用`remove_copy_if`算法结合`not1`否定器。`remove_copy_if`算法会遍历一个范围，并将**不满足**给定谓词的元素复制到目标位置。

![](img/841b7f0aa929ea6656b076d5a9def536_52.png)

![](img/841b7f0aa929ea6656b076d5a9def536_53.png)

![](img/841b7f0aa929ea6656b076d5a9def536_54.png)

![](img/841b7f0aa929ea6656b076d5a9def536_55.png)

![](img/841b7f0aa929ea6656b076d5a9def536_56.png)

![](img/841b7f0aa929ea6656b076d5a9def536_57.png)

![](img/841b7f0aa929ea6656b076d5a9def536_58.png)

![](img/841b7f0aa929ea6656b076d5a9def536_60.png)

以下是关键代码步骤：
1.  定义一个包含数字1到4的向量`v1`和一个空向量`v2`。
2.  使用`remove_copy_if`从`v1`复制元素到`v2`。
3.  传递的谓词是`not1(IsOdd<int>())`，这意味着我们将复制那些**不是奇数**（即为偶数）的元素。
4.  使用`back_inserter`将结果插入`v2`的末尾。

![](img/841b7f0aa929ea6656b076d5a9def536_61.png)

![](img/841b7f0aa929ea6656b076d5a9def536_63.png)

```cpp
std::vector<int> v1 = {1, 2, 3, 4};
std::vector<int> v2;
std::remove_copy_if(v1.begin(), v1.end(), std::back_inserter(v2), std::not1(IsOdd<int>()));
// 现在 v2 包含 {2, 4}
```
这里使用`remove_copy_if`加否定器的组合，其效果等同于直接使用`copy_if`算法。之所以这样演示，是因为在C++标准库早期，`copy_if`曾被遗漏，开发者常通过`remove_copy_if`加否定器来实现相同功能。

![](img/841b7f0aa929ea6656b076d5a9def536_65.png)

![](img/841b7f0aa929ea6656b076d5a9def536_66.png)

![](img/841b7f0aa929ea6656b076d5a9def536_67.png)

![](img/841b7f0aa929ea6656b076d5a9def536_68.png)

### 使用 `not_fn` 与现代容器

![](img/841b7f0aa929ea6656b076d5a9def536_69.png)

![](img/841b7f0aa929ea6656b076d5a9def536_70.png)

![](img/841b7f0aa929ea6656b076d5a9def536_71.png)

![](img/841b7f0aa929ea6656b076d5a9def536_73.png)

接下来，我们使用更现代的否定器`not_fn`，并将输出容器改为双端队列`deque`。

![](img/841b7f0aa929ea6656b076d5a9def536_75.png)

![](img/841b7f0aa929ea6656b076d5a9def536_76.png)

![](img/841b7f0aa929ea6656b076d5a9def536_77.png)

以下是操作步骤：
1.  清空之前的输出容器。
2.  再次使用`remove_copy_if`，但谓词换为`not_fn(IsOdd<int>())`。
3.  将结果插入到一个`deque`中。

![](img/841b7f0aa929ea6656b076d5a9def536_78.png)

![](img/841b7f0aa929ea6656b076d5a9def536_79.png)

![](img/841b7f0aa929ea6656b076d5a9def536_80.png)

![](img/841b7f0aa929ea6656b076d5a9def536_81.png)

![](img/841b7f0aa929ea6656b076d5a9def536_82.png)

```cpp
std::deque<int> dq1;
dq1.clear();
std::remove_copy_if(v1.begin(), v1.end(), std::back_inserter(dq1), std::not_fn(IsOdd<int>()));
// dq1 包含 {2, 4}
```
`not_fn`是C++11引入的，它比`not1`和`not2`更通用，并且后者已被弃用。

### 使用 `copy_if` 与 Lambda 表达式

![](img/841b7f0aa929ea6656b076d5a9def536_84.png)

![](img/841b7f0aa929ea6656b076d5a9def536_85.png)

![](img/841b7f0aa929ea6656b076d5a9def536_86.png)

![](img/841b7f0aa929ea6656b076d5a9def536_87.png)

![](img/841b7f0aa929ea6656b076d5a9def536_88.png)

![](img/841b7f0aa929ea6656b076d5a9def536_89.png)

![](img/841b7f0aa929ea6656b076d5a9def536_90.png)

![](img/841b7f0aa929ea6656b076d5a9def536_91.png)

![](img/841b7f0aa929ea6656b076d5a9def536_92.png)

![](img/841b7f0aa929ea6656b076d5a9def536_93.png)

![](img/841b7f0aa929ea6656b076d5a9def536_94.png)

![](img/841b7f0aa929ea6656b076d5a9def536_95.png)

最后，我们展示最直接的方式：使用`copy_if`算法和Lambda表达式。

![](img/841b7f0aa929ea6656b076d5a9def536_97.png)

![](img/841b7f0aa929ea6656b076d5a9def536_98.png)

![](img/841b7f0aa929ea6656b076d5a9def536_99.png)

以下是实现方式：
1.  清空输出容器。
2.  使用`copy_if`算法，其谓词直接使用一个Lambda表达式来判断数字是否为奇数。
3.  Lambda表达式使用`auto`关键字使其成为通用Lambda。

![](img/841b7f0aa929ea6656b076d5a9def536_101.png)

![](img/841b7f0aa929ea6656b076d5a9def536_102.png)

![](img/841b7f0aa929ea6656b076d5a9def536_103.png)

![](img/841b7f0aa929ea6656b076d5a9def536_104.png)

```cpp
dq1.clear();
std::copy_if(v1.begin(), v1.end(), std::back_inserter(dq1), [](auto number) { return number % 2 != 0; });
// dq1 包含 {1, 3}
```
使用Lambda表达式可以使代码更内联、更清晰，但如果是频繁使用的逻辑，定义独立的函数对象可能更好。

![](img/841b7f0aa929ea6656b076d5a9def536_105.png)

![](img/841b7f0aa929ea6656b076d5a9def536_106.png)

### `print_results` 函数

![](img/841b7f0aa929ea6656b076d5a9def536_108.png)

![](img/841b7f0aa929ea6656b076d5a9def536_109.png)

![](img/841b7f0aa929ea6656b076d5a9def536_110.png)

![](img/841b7f0aa929ea6656b076d5a9def536_111.png)

![](img/841b7f0aa929ea6656b076d5a9def536_112.png)

![](img/841b7f0aa929ea6656b076d5a9def536_113.png)

![](img/841b7f0aa929ea6656b076d5a9def536_115.png)

我们使用的`print_results`函数是一个使用模板模板参数的例子，它可以接受任何顺序容器（如`vector`、`deque`、`list`）并打印其全部内容。

![](img/841b7f0aa929ea6656b076d5a9def536_117.png)

![](img/841b7f0aa929ea6656b076d5a9def536_118.png)

![](img/841b7f0aa929ea6656b076d5a9def536_119.png)

![](img/841b7f0aa929ea6656b076d5a9def536_120.png)

```cpp
template <typename T, template <typename...> class Container>
void print_results(const Container<T>& container) {
    std::copy(container.begin(), container.end(), std::ostream_iterator<T>(std::cout, " "));
    std::cout << std::endl;
}
```

## 示例二：否定器与查找、排序算法

![](img/841b7f0aa929ea6656b076d5a9def536_122.png)

![](img/841b7f0aa929ea6656b076d5a9def536_123.png)

![](img/841b7f0aa929ea6656b076d5a9def536_124.png)

![](img/841b7f0aa929ea6656b076d5a9def536_125.png)

![](img/841b7f0aa929ea6656b076d5a9def536_126.png)

![](img/841b7f0aa929ea6656b076d5a9def536_128.png)

![](img/841b7f0aa929ea6656b076d5a9def536_129.png)

在第二个示例中，我们将看到否定器如何与`find_if`等算法结合，并再次讨论绑定器。

![](img/841b7f0aa929ea6656b076d5a9def536_130.png)

![](img/841b7f0aa929ea6656b076d5a9def536_132.png)

![](img/841b7f0aa929ea6656b076d5a9def536_133.png)

![](img/841b7f0aa929ea6656b076d5a9def536_134.png)

![](img/841b7f0aa929ea6656b076d5a9def536_135.png)

### 自定义函数对象与 `not1`

![](img/841b7f0aa929ea6656b076d5a9def536_137.png)

![](img/841b7f0aa929ea6656b076d5a9def536_138.png)

首先，我们定义一个过于具体的函数对象`IntGreaterThanThree`，它检查一个整数是否大于3。

![](img/841b7f0aa929ea6656b076d5a9def536_139.png)

![](img/841b7f0aa929ea6656b076d5a9def536_140.png)

![](img/841b7f0aa929ea6656b076d5a9def536_141.png)

![](img/841b7f0aa929ea6656b076d5a9def536_142.png)

![](img/841b7f0aa929ea6656b076d5a9def536_144.png)

![](img/841b7f0aa929ea6656b076d5a9def536_145.png)

```cpp
struct IntGreaterThanThree {
    bool operator()(int x) const { return x > 3; }
};
```
然后，我们使用`find_if`算法和`not1`来查找向量中**第一个不大于3**的元素。

![](img/841b7f0aa929ea6656b076d5a9def536_147.png)

![](img/841b7f0aa929ea6656b076d5a9def536_148.png)

![](img/841b7f0aa929ea6656b076d5a9def536_149.png)

![](img/841b7f0aa929ea6656b076d5a9def536_151.png)

![](img/841b7f0aa929ea6656b076d5a9def536_153.png)

```cpp
std::vector<int> vec = {4, 1, 2, 8, 5, 7};
auto it = std::find_if(vec.begin(), vec.end(), std::not1(IntGreaterThanThree()));
// `it` 指向元素 `1`
print_results(it, vec.end()); // 输出: 1 2 8 5 7
```

![](img/841b7f0aa929ea6656b076d5a9def536_155.png)

![](img/841b7f0aa929ea6656b076d5a9def536_157.png)

![](img/841b7f0aa929ea6656b076d5a9def536_158.png)

### 结合绑定器与 `not1`

![](img/841b7f0aa929ea6656b076d5a9def536_160.png)

![](img/841b7f0aa929ea6656b076d5a9def536_161.png)

![](img/841b7f0aa929ea6656b076d5a9def536_162.png)

我们可以不用自定义函数对象，而是使用标准库中的`greater`函数对象和`bind2nd`绑定器，再结合`not1`来实现相同功能。

![](img/841b7f0aa929ea6656b076d5a9def536_164.png)

```cpp
auto it2 = std::find_if(vec.begin(), vec.end(),
                        std::not1(std::bind2nd(std::greater<int>(), 3)));
// `it2` 同样指向元素 `1`
```
`bind2nd`将`greater`的第二个参数绑定为3，`not1`则对其结果取反。注意，`bind2nd`和`bind1st`也已被弃用。

![](img/841b7f0aa929ea6656b076d5a9def536_166.png)

![](img/841b7f0aa929ea6656b076d5a9def536_167.png)

![](img/841b7f0aa929ea6656b076d5a9def536_168.png)

![](img/841b7f0aa929ea6656b076d5a9def536_169.png)

![](img/841b7f0aa929ea6656b076d5a9def536_171.png)

### 使用 `bind` 与 `not_fn`

![](img/841b7f0aa929ea6656b076d5a9def536_173.png)

更现代的方法是使用`bind`函数模板和`not_fn`否定器。

![](img/841b7f0aa929ea6656b076d5a9def536_175.png)

![](img/841b7f0aa929ea6656b076d5a9def536_176.png)

![](img/841b7f0aa929ea6656b076d5a9def536_177.png)

```cpp
using namespace std::placeholders; // 对于 _1
auto it3 = std::find_if(vec.begin(), vec.end(),
                        std::not_fn(std::bind(std::greater<>(), _1, 3)));
// `it3` 指向元素 `1`
```
`bind(std::greater<>(), _1, 3)`创建了一个可调用对象，它等价于`(x) -> x > 3`。`_1`是一个占位符，表示传入的第一个参数。虽然`bind`比旧绑定器灵活，但现代C++更推荐使用Lambda表达式。

![](img/841b7f0aa929ea6656b076d5a9def536_179.png)

![](img/841b7f0aa929ea6656b076d5a9def536_180.png)

### 使用 `find_if_not` 与 Lambda 表达式

![](img/841b7f0aa929ea6656b076d5a9def536_182.png)

![](img/841b7f0aa929ea6656b076d5a9def536_183.png)

![](img/841b7f0aa929ea6656b076d5a9def536_184.png)

最简洁的方式是使用`find_if_not`算法，它内部已经实现了否定逻辑，因此我们直接传递原始的谓词（检查是否大于3）即可。

![](img/841b7f0aa929ea6656b076d5a9def536_186.png)

![](img/841b7f0aa929ea6656b076d5a9def536_187.png)

![](img/841b7f0aa929ea6656b076d5a9def536_188.png)

![](img/841b7f0aa929ea6656b076d5a9def536_190.png)

```cpp
auto it4 = std::find_if_not(vec.begin(), vec.end(),
                            [](auto i) { return i > 3; });
// `it4` 指向元素 `1`
```

![](img/841b7f0aa929ea6656b076d5a9def536_192.png)

![](img/841b7f0aa929ea6656b076d5a9def536_194.png)

![](img/841b7f0aa929ea6656b076d5a9def536_196.png)

### 使用 `not2` 进行排序

![](img/841b7f0aa929ea6656b076d5a9def536_198.png)

`not2`是用于二元函数的否定器。例如，我们可以用它来对向量进行降序排序。

![](img/841b7f0aa929ea6656b076d5a9def536_199.png)

![](img/841b7f0aa929ea6656b076d5a9def536_200.png)

![](img/841b7f0aa929ea6656b076d5a9def536_201.png)

![](img/841b7f0aa929ea6656b076d5a9def536_202.png)

![](img/841b7f0aa929ea6656b076d5a9def536_203.png)

![](img/841b7f0aa929ea6656b076d5a9def536_204.png)

![](img/841b7f0aa929ea6656b076d5a9def536_206.png)

```cpp
std::sort(vec.begin(), vec.end(), std::not2(std::less<int>()));
// `not2(less<int>())` 等价于 `greater<int>()`，因此进行降序排序
```
同样，这里也可以使用`not_fn`来替代`not2`。

![](img/841b7f0aa929ea6656b076d5a9def536_208.png)

![](img/841b7f0aa929ea6656b076d5a9def536_210.png)

![](img/841b7f0aa929ea6656b076d5a9def536_212.png)

![](img/841b7f0aa929ea6656b076d5a9def536_214.png)

```cpp
std::sort(vec.begin(), vec.end(), std::not_fn(std::less<>()));
```

![](img/841b7f0aa929ea6656b076d5a9def536_216.png)

![](img/841b7f0aa929ea6656b076d5a9def536_217.png)

![](img/841b7f0aa929ea6656b076d5a9def536_218.png)

![](img/841b7f0aa929ea6656b076d5a9def536_219.png)

### 改进的 `print_results` 函数

![](img/841b7f0aa929ea6656b076d5a9def536_220.png)

![](img/841b7f0aa929ea6656b076d5a9def536_221.png)

![](img/841b7f0aa929ea6656b076d5a9def536_223.png)

![](img/841b7f0aa929ea6656b076d5a9def536_224.png)

第二个示例中使用的`print_results`函数接受两个迭代器作为参数，并使用`decltype`进行类型推导，从而更通用。

```cpp
template <typename InputIterator>
void print_results(InputIterator first, InputIterator last) {
    if (first != last) {
        std::copy(first, last,
                  std::ostream_iterator<decltype(*first)>(std::cout, " "));
        std::cout << std::endl;
    }
}
```
`decltype(*first)`能够在编译时推导出迭代器所指向元素的类型，使得函数无需显式指定元素类型。

![](img/841b7f0aa929ea6656b076d5a9def536_226.png)

![](img/841b7f0aa929ea6656b076d5a9def536_227.png)

![](img/841b7f0aa929ea6656b076d5a9def536_228.png)

![](img/841b7f0aa929ea6656b076d5a9def536_230.png)

## 总结

![](img/841b7f0aa929ea6656b076d5a9def536_232.png)

本节课中我们一起学习了C++ STL中的否定器适配器。我们介绍了早期的`not1`和`not2`，以及现代的`not_fn`，并通过多个示例展示了它们如何与`remove_copy_if`、`find_if`、`sort`等算法协同工作。我们还回顾了绑定器，比较了旧式`bind1st`/`bind2nd`、`bind`以及Lambda表达式在不同场景下的应用。最后，我们探讨了两种通用的结果打印技术，它们利用了模板模板参数和`decltype`类型推导。掌握这些适配器和技巧，能帮助你编写出更灵活、更现代的C++代码。