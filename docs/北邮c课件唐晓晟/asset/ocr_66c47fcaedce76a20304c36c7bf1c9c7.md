# 迭代器

```
template<class C, typename C::iterator find_last(const C& c, typename C::value_type v) {
// vector反向迭代器，我找到第一个值v位置
typename C::reverse_iterator ri = find(c.rbegin(), c.rend(), v);
if(ri == c.rend()) return c.end(); // 找不到则返回
typename C::iterator i = ri.base();
return --i;
}
```

对reverse_iterator，ri.base()返回一个iterator，指向所指位置之后的一个位置，若没有reverse_iterator，必须使用迭代器写一个显式的值的循环来完成同样的任务

注意：C::reverse_iterator和C::iterator不是同一个类

# 16.3.3 元素访问

与其他容器相比，vector的一个重要特点就是可以方便高效地按照在何顺序访问其中的元素

```
template <class T, class A = allocator<T> > class vector {
public:
reference operator[](size_type n) ; // 不检查下标的访问
const_reference operator[](size_type n) const;
reference at(size_type n) ; // 运行时检查下标
const_reference at(size_type n) const;
reference front() ; // 返回第一个元素
const_reference front() const;
reference back() ; // 返回最后一个元素
const_reference back() const;
...
```

# 元素访问示例

+   下标查询通过operator[]和at()完成，at()进行下标检查，越界时抛出out_of_range异常
+   访问函数返回类型是const_reference或者reference，对了vector<X>，reference就是X&

```
void f(vector<int>& v, int i1, int i2) {
try {
for(int i = 0; i < v.size(); i++) {
// 已经越界访问，运行时可能不检查v[i]
}
v.at(i1) = v.at(i2); // 检查下标
} catch(out_of_range e) {
// 抛出: out_of_range
}
}
```

# 元素访问示例

+   在各种标准序列中，只有vector和deque支持下标
+   试图创建一个越界引用的效果是未定义的

```
void f(vector<double>& v) {
double d = v[v.size()]; // 无定义: 下标越界
list<char> lst;
char c = lst.front(); // 无定义: 表为空
}
```