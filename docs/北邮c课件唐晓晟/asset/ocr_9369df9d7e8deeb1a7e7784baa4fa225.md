# 优先队列—priority_queue

+   - 按默认规则，priority_queue简单地用<运算符做比较，top()返回最大的元素
+   - 实现priority_queue的一种有用方式是采用一个树结构保存元素的相对位置，这能给出O(log(n))代替push()和pop()操作
+   - 按默认测试，priority_queue用一个vector保存其中的元素，对任何能提供front()、push_back()和pop_back()，并能使用随机访问迭代器的序列都可以使用
+   - priority_queue最可能是用一个heap实现

# 17.4 关联容器

+   - 关联容器是指类型定义类群中最常见的也最有用的 一种
+   - 关联容器也常被称作映射(map)，有时也被称作字典(dictionary)；其中每个元素都是对
+   - 给定一个标有关键码的值，我们就请问同一个称为映射的值
+   - 可以将关联数据想象为一个下标不必是整数的数组
+   - map、set类型的关联容器，multiset运行元素表中出现重复关联键，set和multiset可以看成是关联的类数组，其中没有与关键码相关联的值

```
template<class K, class V> class Assoc {
public:
  V& operator[](const K&); // 返回对应于K的V的引用
};
```

# 17.4.1 映射—map

+   - 一个map就是一个(关键码-值)对偶的序列
+   - map提供基于关键码的快速提取操作，关键码具有唯一性，map提供双向迭代器
+   - map要求其关键码类型提供一个小于操作，以保持自己元素的有序性
+   - 对于没有明显顺序的元素，或者不必保持容器有序的情况，可以考虑用hash_map

# 17.4.1.1 类型

```
template<class Key, class T, class Cmp = less<Key>,
  class A = allocator<pair<const Key, T>> > class std::map
{
public:
  typedef Key key_type; // 关键码
  typedef T mapped_type; // 映射值
  typedef pair<const Key, T> value_type; // 元素：是pair
  typedef Cmp key_compare, value_compare;
  typedef typename A::reference reference;
  typedef typename A::const_reference const_reference;
  typedef implementation_defined iterator;
  typedef typename A::size_type size_type;
  typedef typename A::difference_type difference_type;
  typedef std::reverse_iterator<iterator> reverse_iterator;
  typedef std::reverse_iterator<const_iterator> const_reverse_iterator;
};
```