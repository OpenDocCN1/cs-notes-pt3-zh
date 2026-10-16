# 表操作

```
vector<string> fruit;
fruit.push_back("peach");
fruit.push_back("apple");
fruit.push_back("kiwi");
fruit.push_back("pear");
fruit.push_back("starfruit");
fruit.push_back("grape");
sort(fruit.begin(), fruit.end()); // 排序
vector<string>::iterator p1 =
find_if(fruit.begin(), fruit.end(), ...);
vector<string>::iterator p2 =
find_if(p1, fruit.end(), initial_not_p);
// 接下来一个Up为水果结束
fruit.erase(p1, p2);
// 如果p1和p2的位置无关，就是在包括p2
```

注意：erase()要求两个参数，第一个参数是迭代器，iterator与reverse_iterator不是同一个类型，不能混用。删除元素不会改变vector的大小，仅于删除元素之后，vector的迭代器失效。
如果要insert()插入元素，迭代器位置移动，迭代器位置移动，考虑使用list容器

# 16.3.7 元素定位

+   - 一般来说，insert或者erase<|start|>的目标是某个明确的位置(begin()或end())，或者通过查找操作得到的结果(find())，或者在迭代中确定的某个下标
+   - 实际应用中，也可直接使用数值下标(比如数字7)作为索引，方法是c.erase(c.begin()+7)

# 元素定位示例

```
template<class C, void f(C& c){
c.erase(c.begin()+7); // ok
// 但是不支持迭代器的类型不能这样用，list不支持c.begin()+7
c.erase(&c[7]); // 更好
// 但是c[7]可能越界，其它类型如map，vector等不支持
// 比如对于map，迭代器是mapped_type&，value_type&，不能直接用
c.erase(c.begin()+7); // 错误：容器中7没有意义
c.erase(c.back()); // 错误：c.back()返回引用，不是迭代器
c.erase(c.end()-2); // 可以
c.erase(c.begin()+2);
vector<>::reverse_iterator r; // vector::iterator的类型不同
c.erase((c.rbegin()+2).base()); // 转换，但行($19.2.5)
}
```

# 16.3.8 大小和容量

+   - 通常，vector在需要时自动增长。然而，我们也可以直接提供vector增长时所使用的增长因子
+   - 任何时候，vector中的元素个数都可以通过size()获得，并可通过resize()来改变其大小(realloc()类函数)

```
template <class T, class A = allocator<T> > class vector {
public:
size_type size() const; // 元素个数
bool empty() const { return size()==0; } // 是否为空
size_type max_size() const; // 元素最大个数
size_type max_size() const; // 元素最大个数
void resize(size_type n, const T& val = T()); // 改变大小
size_type capacity() const; // 容器已分配存储的大小
void reserve(size_type n); // 改变容器的容量，大小和容量
// keep_max_size()，如果长度error
};
```