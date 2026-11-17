# 020：功能适配器（第二部分）🚀




在本节课中，我们将继续学习C++标准模板库中的功能适配器。上一节我们介绍了绑定器，本节中我们来看看另一种功能适配器——否定器。我们将探讨几种不同的否定器，并通过示例展示其用法。同时，我们也会回顾绑定器，了解它们在不同C++标准版本中的演变。








## 否定器适配器概述





否定器适配器是一种函数对象，它可以封装另一个函数对象，并返回其结果的逻辑非。随着C++标准的发展，出现了几种不同的否定器。




以下是几种主要的否定器：
*   **`not1`**：用于处理一元函数或一元操作。
*   **`not2`**：用于处理二元函数或二元操作。
*   **`not_fn`**（或写作`not_function`）：一个较新的模板，可以同时处理一元或二元函数，无需像`not1`和`not2`那样在名称上区分。





## 示例一：使用否定器与算法



为了演示否定器的工作原理，我们首先创建一个简单的布尔函数对象模板，用于判断一个数字是否为奇数。






```cpp
template <typename T>
struct IsOdd {
    bool operator()(const T& number) const {
        return number % 2 != 0;
    }
};
```
这个`IsOdd`是一个一元函数对象，它接受一个类型为`T`的参数`number`，通过计算`number % 2`来判断是否为奇数（余数不为0则返回`true`）。





我们还将使用一个辅助函数`print_results`来输出计算结果，它利用了模板模板参数的技术。





### 使用 `remove_copy_if` 与 `not1`

首先，我们使用`remove_copy_if`算法结合`not1`否定器。`remove_copy_if`算法会遍历一个范围，并将**不满足**给定谓词的元素复制到目标位置。









以下是关键代码步骤：
1.  定义一个包含数字1到4的向量`v1`和一个空向量`v2`。
2.  使用`remove_copy_if`从`v1`复制元素到`v2`。
3.  传递的谓词是`not1(IsOdd<int>())`，这意味着我们将复制那些**不是奇数**（即为偶数）的元素。
4.  使用`back_inserter`将结果插入`v2`的末尾。



```cpp
std::vector<int> v1 = {1, 2, 3, 4};
std::vector<int> v2;
std::remove_copy_if(v1.begin(), v1.end(), std::back_inserter(v2), std::not1(IsOdd<int>()));
// 现在 v2 包含 {2, 4}
```
这里使用`remove_copy_if`加否定器的组合，其效果等同于直接使用`copy_if`算法。之所以这样演示，是因为在C++标准库早期，`copy_if`曾被遗漏，开发者常通过`remove_copy_if`加否定器来实现相同功能。





### 使用 `not_fn` 与现代容器





接下来，我们使用更现代的否定器`not_fn`，并将输出容器改为双端队列`deque`。




以下是操作步骤：
1.  清空之前的输出容器。
2.  再次使用`remove_copy_if`，但谓词换为`not_fn(IsOdd<int>())`。
3.  将结果插入到一个`deque`中。






```cpp
std::deque<int> dq1;
dq1.clear();
std::remove_copy_if(v1.begin(), v1.end(), std::back_inserter(dq1), std::not_fn(IsOdd<int>()));
// dq1 包含 {2, 4}
```
`not_fn`是C++11引入的，它比`not1`和`not2`更通用，并且后者已被弃用。

### 使用 `copy_if` 与 Lambda 表达式













最后，我们展示最直接的方式：使用`copy_if`算法和Lambda表达式。




以下是实现方式：
1.  清空输出容器。
2.  使用`copy_if`算法，其谓词直接使用一个Lambda表达式来判断数字是否为奇数。
3.  Lambda表达式使用`auto`关键字使其成为通用Lambda。





```cpp
dq1.clear();
std::copy_if(v1.begin(), v1.end(), std::back_inserter(dq1), [](auto number) { return number % 2 != 0; });
// dq1 包含 {1, 3}
```
使用Lambda表达式可以使代码更内联、更清晰，但如果是频繁使用的逻辑，定义独立的函数对象可能更好。



### `print_results` 函数








我们使用的`print_results`函数是一个使用模板模板参数的例子，它可以接受任何顺序容器（如`vector`、`deque`、`list`）并打印其全部内容。





```cpp
template <typename T, template <typename...> class Container>
void print_results(const Container<T>& container) {
    std::copy(container.begin(), container.end(), std::ostream_iterator<T>(std::cout, " "));
    std::cout << std::endl;
}
```

## 示例二：否定器与查找、排序算法








在第二个示例中，我们将看到否定器如何与`find_if`等算法结合，并再次讨论绑定器。






### 自定义函数对象与 `not1`



首先，我们定义一个过于具体的函数对象`IntGreaterThanThree`，它检查一个整数是否大于3。







```cpp
struct IntGreaterThanThree {
    bool operator()(int x) const { return x > 3; }
};
```
然后，我们使用`find_if`算法和`not1`来查找向量中**第一个不大于3**的元素。






```cpp
std::vector<int> vec = {4, 1, 2, 8, 5, 7};
auto it = std::find_if(vec.begin(), vec.end(), std::not1(IntGreaterThanThree()));
// `it` 指向元素 `1`
print_results(it, vec.end()); // 输出: 1 2 8 5 7
```




### 结合绑定器与 `not1`




我们可以不用自定义函数对象，而是使用标准库中的`greater`函数对象和`bind2nd`绑定器，再结合`not1`来实现相同功能。


```cpp
auto it2 = std::find_if(vec.begin(), vec.end(),
                        std::not1(std::bind2nd(std::greater<int>(), 3)));
// `it2` 同样指向元素 `1`
```
`bind2nd`将`greater`的第二个参数绑定为3，`not1`则对其结果取反。注意，`bind2nd`和`bind1st`也已被弃用。






### 使用 `bind` 与 `not_fn`


更现代的方法是使用`bind`函数模板和`not_fn`否定器。




```cpp
using namespace std::placeholders; // 对于 _1
auto it3 = std::find_if(vec.begin(), vec.end(),
                        std::not_fn(std::bind(std::greater<>(), _1, 3)));
// `it3` 指向元素 `1`
```
`bind(std::greater<>(), _1, 3)`创建了一个可调用对象，它等价于`(x) -> x > 3`。`_1`是一个占位符，表示传入的第一个参数。虽然`bind`比旧绑定器灵活，但现代C++更推荐使用Lambda表达式。



### 使用 `find_if_not` 与 Lambda 表达式




最简洁的方式是使用`find_if_not`算法，它内部已经实现了否定逻辑，因此我们直接传递原始的谓词（检查是否大于3）即可。





```cpp
auto it4 = std::find_if_not(vec.begin(), vec.end(),
                            [](auto i) { return i > 3; });
// `it4` 指向元素 `1`
```




### 使用 `not2` 进行排序


`not2`是用于二元函数的否定器。例如，我们可以用它来对向量进行降序排序。








```cpp
std::sort(vec.begin(), vec.end(), std::not2(std::less<int>()));
// `not2(less<int>())` 等价于 `greater<int>()`，因此进行降序排序
```
同样，这里也可以使用`not_fn`来替代`not2`。





```cpp
std::sort(vec.begin(), vec.end(), std::not_fn(std::less<>()));
```





### 改进的 `print_results` 函数





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





## 总结

![](img/841b7f0aa929ea6656b076d5a9def536_232.png)

本节课中我们一起学习了C++ STL中的否定器适配器。我们介绍了早期的`not1`和`not2`，以及现代的`not_fn`，并通过多个示例展示了它们如何与`remove_copy_if`、`find_if`、`sort`等算法协同工作。我们还回顾了绑定器，比较了旧式`bind1st`/`bind2nd`、`bind`以及Lambda表达式在不同场景下的应用。最后，我们探讨了两种通用的结果打印技术，它们利用了模板模板参数和`decltype`类型推导。掌握这些适配器和技巧，能帮助你编写出更灵活、更现代的C++代码。