
## 提升示例

- 几乎就是标准库中的 accumulate
  - 为了简洁我稍微简化了一下
  - （更多通用性和细节参见 21.5）
- 适用于
  - 数组
  - 向量
  - 列表
  - 输入流
  - ...
- 运行速度与“手工编写”的代码一样快
  - 在良好的内联条件下
- 代码对其数据的要求变得明确
  - 我们能更好地理解代码

## STL

- 是 ISO C++ 标准库的一部分
- 大部分是非数值的
  - 只有 4 个标准算法专门进行数值计算
    - Accumulate、inner_product、partial_sum、adjacent_difference
  - 处理文本数据以及数值数据
    - 例如 string
  - 涉及代码和数据的组织
    - 内置类型、用户自定义类型和数据结构
- 优化磁盘访问是其最初的用途之一
  - 性能始终是一个关键问题

## STL

![](img/af430dff16b82a0fe61ce7dee05dcf9c_156_0.png)

- 由 Alex Stepanov 设计
- 总体目标：以最通用、最高效、最灵活的方式表示概念（思想、算法）
  - 在代码中分别表示不同的概念
  - 在有意义的地方自由组合概念
- 总体目标是让编程“像数学一样”
  - 甚至“良好的编程就是数学”
  - 适用于整数、浮点数、多项式等……

## 基本模型

- 算法
  - sort、find、search、copy 等……

- 容器
  - vector、list、map、hash_map 等……

![](img/af430dff16b82a0fe61ce7dee05dcf9c_157_0.png)

- 关注点分离
  - 算法操作数据，但不知道容器的存在
  - 容器存储数据，但不知道算法的存在
  - 算法和容器通过迭代器交互
  - 每个容器都有自己的迭代器类型

## STL

- 一个 ISO C++ 标准框架，包含约 10 个容器和约 60 个算法，通过迭代器连接在一起
  - 其他组织也提供更多遵循 STL 风格的容器和算法
    - Boost.org、Microsoft、SGI 等……
- 可能是目前最著名、应用最广泛的泛型编程示例

## STL

- 如果你了解了基本概念和几个示例，就可以使用其余部分
- 文档
  - SGI
    - http://www.sgi.com/tech/stl/ （推荐，因为清晰）
  - Dinkumware
    - http://www.dinkumware.com/refxcpp.html （注意有多个库版本）
  - Rogue Wave
    - http://www.roguewave.com/support/docs/sourcepro/stdlibug/index.html
- 更易获取但不太完整的文档
  - 附录 B

## 基本模型

- 一对迭代器定义了一个序列
  - 起始迭代器（指向第一个元素——如果有的话）
  - 结束迭代器（指向最后一个元素之后的位置）

![](img/af430dff16b82a0fe61ce7dee05dcf9c_160_0.png)

- 迭代器是一种支持“迭代器操作”的类型
  - ++ 转到下一个元素
  - * 获取值
  - == 这个迭代器是否与那个迭代器指向同一个元素？
- 一些迭代器支持更多操作（例如 --、+ 和 [ ]）

## 最简单的算法：**find()**

![](img/af430dff16b82a0fe61ce7dee05dcf9c_162_0.png)

> _// 查找等于某个值的第一个元素_

```
template<class In, class T>
In find(In first, In last, const T& val)
{
    while (first!=last && *first != val) ++first;
    return first;
}
```

```
void f(vector<int>& v, int x)      // find an int in a vector
{
    vector<int>::iterator p = find(v.begin(),v.end(),x);
    if (p!=v.end()) { /* we found x */ }
    // ...
}
```

我们可以忽略（“抽象掉”）容器之间的差异

## find()

对元素类型和容器类型均通用

```
void f(vector<int>& v, int x)          // works for vector of ints
{
    vector<int>::iterator p = find(v.begin(),v.end(),x);
    if (p!=v.end()) {/* we found x */}
    // ...
}
```

```
void f(list<string>& v, string x)        // works for list of strings
{
    list<string>::iterator p = find(v.begin(),v.end(),x);
    if (p!=v.end()) {/* we found x */}
    // ...
}
```

```
void f(set<double>& v, double x)         // works of set of doubles
{
    set<double>::iterator p = find(v.begin(),v.end(),x);
    if (p!=v.end()) {/* we found x */}
    // ...
}
```
