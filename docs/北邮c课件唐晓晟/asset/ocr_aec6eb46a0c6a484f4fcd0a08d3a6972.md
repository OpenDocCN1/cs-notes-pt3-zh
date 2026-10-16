# 16.3.10 协助函数

+   用==和!=可以比较两个vector

```
template <class T, class A>
bool std::operator==(const vector<T,A>& x, const vector<T,A>& y);
template <class T, class A>
bool std::operator!=(const vector<T,A>& x, const vector<T,A>& y);
```

+   标准库还提供了!=、<=、>=等协助函数

# 16.3.11 vector<bool>

+   标准库还提供了专门化vector(bool)，作为bool类里的紧凑vector，bool变量可以寻址，所以它至少要占一个字节

+   通常的vector操作都可对vector(bool)使用，而且保持了它们原来的意义

+   标准库还提供布尔值集合bitset，带有一组布尔集合运算

# 16.4 忠告

+   [1] 利用标准库功能，以维持可移植性

+   [2] 不要自行定义标准库的功能

+   [3] 决不要认为标准库比什么都好

+   [4] 在定义一种新功能时，应考虑它是否能够纳入标准库所提供的框架中

+   [5] 记过标准库功能都定义在名字空间std

+   [6] 通过包含标准库头文件声明其功能，不要自行另行显示声明

# 忠告

+   [7] 利用后插抽取的优点

+   [8] 避免免费的午餐

+   [9] 与自己写按照反向顺序的显式循环相比，最好是用引用反向迭代器的算法

+   [10] 用base()从reverse_iterator抽出iterator

+   [11] 通过引用传递容器

+   [12] 用迭代器类型，如list<char>::iterator，而不要采用索引容器元素的指针