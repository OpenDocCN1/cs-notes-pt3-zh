# 013：有序和无序关联容器

![](img/a8f3bb8fd2f44bc6c18390af20de6987_1.png)

![](img/a8f3bb8fd2f44bc6c18390af20de6987_2.png)

![](img/a8f3bb8fd2f44bc6c18390af20de6987_4.png)

![](img/a8f3bb8fd2f44bc6c18390af20de6987_6.png)

在本节课中，我们将要学习C++标准模板库中的另一种有序关联容器——`map`，以及它的兄弟`multimap`。我们将探讨如何使用`map`，并通过一些非常有趣的示例来演示它们的结构和功能。此外，我们也会简要了解无序关联容器。

![](img/a8f3bb8fd2f44bc6c18390af20de6987_8.png)

## 概述与代码位置

![](img/a8f3bb8fd2f44bc6c18390af20de6987_10.png)

![](img/a8f3bb8fd2f44bc6c18390af20de6987_12.png)

上一节我们介绍了有序关联容器`set`，本节中我们来看看`map`。

![](img/a8f3bb8fd2f44bc6c18390af20de6987_14.png)

![](img/a8f3bb8fd2f44bc6c18390af20de6987_16.png)

首先，让我们看看在哪里可以找到本课使用的代码。代码位于我的GitHub账户的C++ STL S05仓库中，我们将重点关注示例5.5、5.6和5.7。

![](img/a8f3bb8fd2f44bc6c18390af20de6987_17.png)

![](img/a8f3bb8fd2f44bc6c18390af20de6987_19.png)

## 理解Map

`map`是一种有序关联容器，它将键对象与值对象关联起来。它被称为**对关联容器**，因为它的值类型实际上实现为一个包含常量键和值类型的`pair`。

![](img/a8f3bb8fd2f44bc6c18390af20de6987_21.png)

![](img/a8f3bb8fd2f44bc6c18390af20de6987_22.png)

需要记住的是，与`set`一样，键是常量。在迭代过程中不能更改它，因为这会导致底层用于排序的红黑树（一种平衡的二叉搜索树）混乱。对于`map`，键必须是唯一的，就像`set`一样。键不一定是整数，它可以是任何类型，例如字符串，只要该类型能够使用小于运算符进行比较。

以下是传递给`map`模板的各种参数：
*   键类型（必需）
*   值类型（必需）
*   比较器操作（可选，默认为`std::less`）
*   分配器（可选，默认为全局堆的`new`和`delete`）

`map`的关键特性是：向`map`中插入新元素不会使指向现有元素的迭代器失效（因为它像`set`一样是树实现的）。从`map`中擦除元素也不会使任何迭代器失效，当然，你正在擦除的那个元素对应的迭代器除外。

如果你想使用`map`，必须提供键类型和值类型。如果需要，你也可以选择提供比较函数。在我们的示例中，将使用默认的`less`操作，但你也可以像对`set`那样传递`greater`来按不同顺序排序。

![](img/a8f3bb8fd2f44bc6c18390af20de6987_24.png)

## 示例一：单词计数

![](img/a8f3bb8fd2f44bc6c18390af20de6987_26.png)

这是一个非常酷的示例。我们将处理一个字符串向量，内容是著名的短语：“now is the time for all good people to come to the aid of their party”。我们将统计每个单词在输入中出现的次数。

我们首先定义一个从`string`到`int`的映射`word_map`，用于跟踪每个单词的出现次数。

![](img/a8f3bb8fd2f44bc6c18390af20de6987_28.png)

以下是填充映射的方法：
*   我们使用基于范围的`for`循环遍历单词列表。
*   对于列表中的每个单词，我们将其作为键索引到`word_map`中，并递增对应的值（计数）。
*   由于C++初始化器的特性，映射中所有的`int`值都会以0开始，所以我们不需要自己初始化。

![](img/a8f3bb8fd2f44bc6c18390af20de6987_30.png)

![](img/a8f3bb8fd2f44bc6c18390af20de6987_31.png)

![](img/a8f3bb8fd2f44bc6c18390af20de6987_33.png)

![](img/a8f3bb8fd2f44bc6c18390af20de6987_35.png)

```cpp
std::map<std::string, int> word_map;
for (const auto& word : word_list) {
    ++word_map[word]; // 类似于关联数组
}
```

填充映射后，我们打印结果，显示每个单词及其出现次数。

![](img/a8f3bb8fd2f44bc6c18390af20de6987_37.png)

![](img/a8f3bb8fd2f44bc6c18390af20de6987_38.png)

接下来，我们使用两种方法计算单词总数：函数对象和Lambda表达式。

![](img/a8f3bb8fd2f44bc6c18390af20de6987_40.png)

**使用函数对象：**
我们创建一个名为`total_it`的函数对象（仿函数）。它内部保存一个计数器，每次调用时，将传入的`pair`（即`map`的值类型）的第二个值（计数）加到内部计数器上。然后我们使用`std::for_each`算法遍历`word_map`，传入`total_it`的一个实例。

![](img/a8f3bb8fd2f44bc6c18390af20de6987_42.png)

**使用Lambda表达式：**
我们使用`std::for_each`算法和一个Lambda函数重新实现求和。Lambda函数捕获外部变量`total`的引用，并在每次调用时更新它。这使得代码更加简洁，无需定义单独的仿函数结构。

![](img/a8f3bb8fd2f44bc6c18390af20de6987_44.png)

![](img/a8f3bb8fd2f44bc6c18390af20de6987_46.png)

运行代码后，输出按字母顺序排列（因为`map`是有序的），显示了每个单词的出现次数，并使用两种方法计算出的总单词数相同。

![](img/a8f3bb8fd2f44bc6c18390af20de6987_48.png)

![](img/a8f3bb8fd2f44bc6c18390af20de6987_50.png)

## 示例二：字典操作

![](img/a8f3bb8fd2f44bc6c18390af20de6987_51.png)

这个示例展示了`map`的其他一些特性。我们创建一个简单的英德字典。

![](img/a8f3bb8fd2f44bc6c18390af20de6987_53.png)

![](img/a8f3bb8fd2f44bc6c18390af20de6987_54.png)

![](img/a8f3bb8fd2f44bc6c18390af20de6987_56.png)

以下是操作`map`的几种方式：
*   使用下标运算符`[]`进行赋值：`dictionary["shoe"] = "Schuh";`
*   创建一个`value_type`（即`pair`）并使用`insert`方法插入：`dictionary.insert(std::make_pair("yes", "ja"));`

![](img/a8f3bb8fd2f44bc6c18390af20de6987_58.png)

我们定义了一个打印仿函数来输出字典内容。然后，我们演示了如何查找和删除元素：
1.  使用`find`方法查找键为`"yes"`的元素，返回一个迭代器。
2.  如果找到了（迭代器不等于`end()`），则使用`erase`方法删除该元素。

![](img/a8f3bb8fd2f44bc6c18390af20de6987_60.png)

最后，我们再次打印字典，这次使用Lambda函数替代仿函数进行输出，使代码更紧凑。

## 转向Multimap

![](img/a8f3bb8fd2f44bc6c18390af20de6987_62.png)

![](img/a8f3bb8fd2f44bc6c18390af20de6987_63.png)

![](img/a8f3bb8fd2f44bc6c18390af20de6987_65.png)

到目前为止，我们讨论的都是`map`，它要求键唯一。现在我们将注意力转向`multimap`。

![](img/a8f3bb8fd2f44bc6c18390af20de6987_67.png)

与`set`和`multiset`的关系类似，`map`只能有唯一的键，而`multimap`可以包含重复的键。`multimap`也是一个有序的对关联容器，其模板参数与`map`相同，唯一的真正区别就是允许重复键。

![](img/a8f3bb8fd2f44bc6c18390af20de6987_69.png)

![](img/a8f3bb8fd2f44bc6c18390af20de6987_71.png)

## 示例三：使用Multimap

![](img/a8f3bb8fd2f44bc6c18390af20de6987_73.png)

这是一个有趣的例子，展示了`multimap`的许多功能。我们创建一个`multimap<string, string>`来存储人名（名作为键，姓作为值）。

我们首先插入几个`value_type`对。为了优化插入效率，我们演示了如何使用提示迭代器：当你知道要插入的元素应该放在容器末尾附近时，可以向`insert`方法传递一个迭代器（如`end()`）作为提示，这可能会提高插入效率。

我们还展示了如何插入一个范围的值。我们创建一个`vector`，里面包含多个`value_type`对，然后使用`insert`方法将整个`vector`的范围插入到`multimap`中。

![](img/a8f3bb8fd2f44bc6c18390af20de6987_75.png)

![](img/a8f3bb8fd2f44bc6c18390af20de6987_76.png)

![](img/a8f3bb8fd2f44bc6c18390af20de6987_77.png)

我们重载了流插入运算符`<<`，使其能够方便地打印整个`multimap`或一个迭代器范围。

![](img/a8f3bb8fd2f44bc6c18390af20de6987_79.png)

![](img/a8f3bb8fd2f44bc6c18390af20de6987_80.png)

![](img/a8f3bb8fd2f44bc6c18390af20de6987_81.png)

![](img/a8f3bb8fd2f44bc6c18390af20de6987_83.png)

以下是`multimap`的一些关键操作：
*   **查找所有相同键的元素**：使用`equal_range`方法，它返回一个`pair`，包含指向该键范围的开始和结束的迭代器。
*   **计数特定键的数量**：使用`count`方法。
*   **删除特定键的所有元素**：使用`erase`方法并传入从`equal_range`获得的迭代器范围。

![](img/a8f3bb8fd2f44bc6c18390af20de6987_85.png)

在示例中，我们查找所有名为“Kim”的人，打印他们的数量和详细信息，然后删除所有名为“Kim”的记录，并打印更新后的列表。最后，我们查找“Kurt”并打印他的姓氏。

![](img/a8f3bb8fd2f44bc6c18390af20de6987_86.png)

![](img/a8f3bb8fd2f44bc6c18390af20de6987_87.png)

![](img/a8f3bb8fd2f44bc6c18390af20de6987_89.png)

## 优化：Emplace与Insert

![](img/a8f3bb8fd2f44bc6c18390af20de6987_91.png)

![](img/a8f3bb8fd2f44bc6c18390af20de6987_93.png)

![](img/a8f3bb8fd2f44bc6c18390af20de6987_94.png)

我们继续使用`multimap`示例，但这次演示`insert`和`emplace`之间的区别，以及优化的重要性。

![](img/a8f3bb8fd2f44bc6c18390af20de6987_96.png)

![](img/a8f3bb8fd2f44bc6c18390af20de6987_98.png)

当我们使用`insert`插入`value_type`时，会发生以下步骤：构造临时`pair`对象，可能触发拷贝/移动构造函数和析构函数，这对于具有昂贵复制语义的类型（如我们自定义的`SimpleString`类）来说开销很大。

![](img/a8f3bb8fd2f44bc6c18390af20de6987_100.png)

![](img/a8f3bb8fd2f44bc6c18390af20de6987_102.png)

![](img/a8f3bb8fd2f44bc6c18390af20de6987_103.png)

![](img/a8f3bb8fd2f44bc6c18390af20de6987_104.png)

相比之下，`emplace`方法直接在容器内部构造元素，接受用于构造键和值的参数。这避免了创建临时对象，效率更高。代码显示，使用`emplace`时，只调用了必要的构造函数，没有额外的拷贝或移动操作。

![](img/a8f3bb8fd2f44bc6c18390af20de6987_106.png)

![](img/a8f3bb8fd2f44bc6c18390af20de6987_108.png)

![](img/a8f3bb8fd2f44bc6c18390af20de6987_109.png)

![](img/a8f3bb8fd2f44bc6c18390af20de6987_111.png)

同样，也有`emplace_hint`方法，它类似于带提示迭代器的`insert`，但使用`emplace`的语义进行原地构造。

![](img/a8f3bb8fd2f44bc6c18390af20de6987_113.png)

因此，建议在可能的情况下优先使用`emplace`而非`insert`，以获得更好的性能。

![](img/a8f3bb8fd2f44bc6c18390af20de6987_115.png)

![](img/a8f3bb8fd2f44bc6c18390af20de6987_116.png)

![](img/a8f3bb8fd2f44bc6c18390af20de6987_117.png)

![](img/a8f3bb8fd2f44bc6c18390af20de6987_119.png)

![](img/a8f3bb8fd2f44bc6c18390af20de6987_121.png)

## 无序关联容器简介

![](img/a8f3bb8fd2f44bc6c18390af20de6987_123.png)

![](img/a8f3bb8fd2f44bc6c18390af20de6987_125.png)

![](img/a8f3bb8fd2f44bc6c18390af20de6987_126.png)

到目前为止，我们讨论的都是有序关联容器，它们底层由红黑树实现。现在我们将展示一个无序关联容器的例子。

![](img/a8f3bb8fd2f44bc6c18390af20de6987_128.png)

![](img/a8f3bb8fd2f44bc6c18390af20de6987_129.png)

![](img/a8f3bb8fd2f44bc6c18390af20de6987_130.png)

无序关联容器（如`unordered_map`）在API上与有序容器类似，关键区别在于它们不维护元素的顺序。有序容器使用红黑树和小于比较，而无序容器使用哈希表和哈希函数。

![](img/a8f3bb8fd2f44bc6c18390af20de6987_132.png)

`unordered_map`的模板参数包括：
*   键类型
*   值类型
*   哈希函数对象（默认为`std::hash`）
*   谓词函数对象（用于哈希冲突时比较键是否相等，默认为`std::equal_to`）
*   分配器

![](img/a8f3bb8fd2f44bc6c18390af20de6987_134.png)

## 示例四：使用Unordered_Map

![](img/a8f3bb8fd2f44bc6c18390af20de6987_136.png)

我们修改之前的单词计数示例，将`map`替换为`unordered_map`。代码大部分相同，我们遍历单词列表并将元素插入到`unordered_map`中。区别在于，现在元素存储的位置由哈希函数决定，而不是按键排序。

![](img/a8f3bb8fd2f44bc6c18390af20de6987_138.png)

当我们打印`unordered_map`的内容时，元素没有特定的顺序，只是按照它们在哈希表中的位置输出。

如果我们希望看到排序后的结果，可以将`unordered_map`的内容复制到一个`vector`中，然后对`vector`进行排序。示例中我们使用`std::sort`并传入`greater`仿函数进行降序排序。

![](img/a8f3bb8fd2f44bc6c18390af20de6987_140.png)

![](img/a8f3bb8fd2f44bc6c18390af20de6987_142.png)

![](img/a8f3bb8fd2f44bc6c18390af20de6987_143.png)

最后，我们像之前一样使用Lambda函数计算单词总数。

运行代码后，首先输出的是无序的单词计数，之后输出的是排序后的版本。

![](img/a8f3bb8fd2f44bc6c18390af20de6987_145.png)

![](img/a8f3bb8fd2f44bc6c18390af20de6987_146.png)

![](img/a8f3bb8fd2f44bc6c18390af20de6987_147.png)

![](img/a8f3bb8fd2f44bc6c18390af20de6987_148.png)

![](img/a8f3bb8fd2f44bc6c18390af20de6987_150.png)

![](img/a8f3bb8fd2f44bc6c18390af20de6987_151.png)

![](img/a8f3bb8fd2f44bc6c18390af20de6987_153.png)

## 总结

![](img/a8f3bb8fd2f44bc6c18390af20de6987_155.png)

![](img/a8f3bb8fd2f44bc6c18390af20de6987_156.png)

![](img/a8f3bb8fd2f44bc6c18390af20de6987_157.png)

本节课中我们一起学习了C++ STL中的有序关联容器`map`和`multimap`。我们了解了`map`如何关联键值对，并且键是唯一的。通过单词计数和字典示例，我们实践了插入、查找、删除和遍历操作。我们还探讨了`multimap`，它允许重复的键，并学习了如何使用`equal_range`来处理重复键。

![](img/a8f3bb8fd2f44bc6c18390af20de6987_159.png)

我们比较了`insert`和`emplace`，认识到`emplace`在避免不必要的对象拷贝方面更具效率。最后，我们简要介绍了无序关联容器`unordered_map`，它使用哈希表实现，不维护元素顺序，但在平均情况下提供更快的访问速度。

希望这些示例能帮助你深入理解STL关联容器的强大功能和灵活性。