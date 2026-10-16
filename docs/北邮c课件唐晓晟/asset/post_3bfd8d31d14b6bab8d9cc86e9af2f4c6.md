
## 16.3.4 构造函数

```
template <class T, class Allocator = allocator<T> > class vector {
public:
    explicit vector(const A& a = A());
    explicit vector(size_type n, const T& val = T(), const A& a = A());
    // n个val的副本
    template <class In> // In 依赖输入迭代器（§19.2.1）
    vector(In first, In last, const A& a = A()); // first到last迭代器
    vector(const vector& x);
    vector& operator=(const vector& x);
    template <class In> // In 依赖输入迭代器（§19.2.1）
    void assign(In first, In last); // 将[first,last)范围迭代
    void assign(size_type n, const T& val); // n个val副本
    // ...
};
// vector提供了完整的一组构造、析构和赋值操作
```

### 构造函数示例

vector提供了两种有元素的构造访问，但是修改它的值的作用是相当昂贵的，因此我们在创建vector时通常给出一个初始大小。

```
vector<Record> vr(10000);
void f(int &i, int s) {
    vector<int> vi(s);
    vector<double>* p = new vector<double>(s2);
}
// 这种方式在vector元素都不是默认构造的类型时构造效率很低。
// 如果没有默认构造函数，就不能创建这个类型的空vector的副本
class Num {
public:
    Num(long);
};
vector<Num> v1(1000); // 错误：无法默认构造
vector<Num> v2(1000, Num(0)); // ok
```

### 构造函数示例

vector的大小也可以通过初始元素的集合隐式给定，这样做需要给vector提供一个值的序列。此时，vector的构造函数会调整vector的大小。

```
void f(const list<X>& lst)
{
    vector<X> v1(lst.begin(), lst.end()); // 从列表构造
    char p[] = "...";
    vector<char> v2(p, p + sizeof(p)-1); // 从C风格字符串构造
}
```

### 构造函数示例

复制构造函数和复制赋值运算符将拷贝vector的所有元素。其代价可能会很高，所以vector通常采用引用传递。

```
void f(vector<int>&); // 非常规
void f2(const vector<int>&); // 常见风格
void f3(vector<int>); // 非常规
void h()
{
    vector<int> v(10000);
    // ...
    f1(v); // 传递引用
    f2(v); // 传递引用
    f3(v); // 至少复制10000个元素的副本操作
}
```

### 构造函数示例

- assign函数可以被用来一次性地为vector中的各个元素赋值，这样做时，没有与其大小的构造函数或者拷贝构造函数
- 注意：赋值将完全改变一个向量里的全部元素，所有的老元素都被删除，重新装入

```
class Book {
public:
  void f(vector<Num>& vn, vector<char>& vc,
         vector<Book>& vb, list<Book>& lb)
  {
    vn.assign(10, Num(0)); // 对10个Num(0)的vn赋值
    char s[] = "literal";
    vc.assign(s, &s[sizeof(s)-1]); // 用literal给vc赋值
    vb.assign(lb.begin(), lb.end()); // 用重复的元素赋值
  }
};
```

## 16.3.5 堆栈操作

- 最常见的情况是，我们把vector看作一种可以直接通过下标访问元素的连续数据结构
- vector的push_back将想象地导致vector的size()增长，所以不会溢出，但是可能扩容

```
template <class T, class A = allocator<T> > class vector {
public:
  void push_back(const T& x); // 在最后加入
  void pop_back(); // 删除最后元素
  // ...
};
```

### 堆栈操作

- 每次调用push_back时vector就增长一个元素，这个元素被加到最后，所以s.size()就是元素个数
- vector可以被看为realloc()的更通用、更优美而且经常降低效率的替代机制

```
void f(vector<char>& s){
  s.push_back('a');
  s.push_back('b');
  s.push_back('c');
  s.pop_back(); // 注意，并不返回数值，只是弹出
  if (s.size()!=1) error("impossible");
  s.pop_back();
  if (s.back() != 'a') error("should never happen");
}
```

## 16.3.6 表操作

- push_back()、pop_back()和back()操作使vector可以有效地作为堆栈使用
- 然而，在vector的中间增加元素，从vector里删除元素时也很有用

```
template <class T, class A = allocator<T> > class vector {
public:
  iterator insert(iterator pos, const T& x); // 在pos游标处插入x
  void insert(iterator pos, size_type n, const T& x); // 在pos插入n个x
  template <class In> void insert(iterator pos, In first, In last);
  // 从范围插入迭代器[first,last)中的元素
  iterator erase(iterator pos); // 删除pos处的元素
  iterator erase(iterator first, iterator last); // 删除一段元素
  void clear(); // 删除所有元素
  // 如果insert或erase使指向部分元素的迭代器失效，则所有失效的迭代器指向被删除的最后元素之后的那个元素，这两种操作都有可能导致迭代器指向另外的元素
```

### 表操作

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

## 16.3.7 元素定位

- 一般来说，insert或者erase的目标是某个明确的位置(begin()或end())，或者通过查找操作得到的结果(find())，或者在迭代中确定的某个下标
- 实际应用中，也可直接使用数值下标(比如数字7)作为索引，方法是c.erase(c.begin()+7)

### 元素定位示例

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
c.erase((c.rbegin()+2).base()); // 转换，但行(§19.2.5)
}
```

## 16.3.8 大小和容量

- 通常，vector在需要时自动增长。然而，我们也可以直接提供vector增长时所使用的增长因子
- 任何时候，vector中的元素个数都可以通过size()获得，并可通过resize()来改变其大小(realloc()类函数)

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
