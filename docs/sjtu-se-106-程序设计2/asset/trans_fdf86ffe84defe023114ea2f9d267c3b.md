

## 算法与迭代器

- 迭代器指向（引用、表示）序列中的一个元素
- 序列的末尾是“最后一个元素之后的位置”
  - *而不是*“最后一个元素”
  - 这对于优雅地表示空序列是必要的
  - “最后一个元素之后的位置”不是元素
    - 你可以将指向它的迭代器进行比较
    - 你不能解引用它（读取它的值）
- 返回序列的末尾是“未找到”或“未成功”的标准惯用法

![](img/af430dff16b82a0fe61ce7dee05dcf9c_164_0.png)

## 谓词

- 谓词（单参数）是一个函数或函数对象，它接受一个参数并返回 `bool`
- 例如
  - 一个函数

```cpp
bool odd(int i) { return i % 2; } // % is the remainder (modulo) operator
odd(7);                            // call odd: is 7 odd?
```

  - 一个函数对象

```cpp
struct Odd {
    bool operator()(int i) const { return i % 2; }
};

Odd odd;        // make an object odd of type Odd
odd(7);         // call odd: is 7 odd?
```

## 函数对象

- 一个使用状态的具体示例

```
template<class T> struct Less_than {
    T val;     // value to compare with
    Less_than(int x) : val(x) { }
    bool operator()(const T& x) const { return x < val; }
};

// find x < 43 in vector<int>:
p=find_if(v.begin(), v.end(), Less_than(43));

// find x “perfection” in list<string>:
q=find_if(ls.begin(), ls.end(), Less_than("perfection"));
```

## 函数对象

- 一种非常高效的技术
  - 内联非常容易
    - 并且对当前的编译器非常有效
  - 比等价的函数更快
    - 而且有时你无法编写等价的函数
- STL 中策略参数化的主要方法
- 在 C++ 中模拟函数式编程技术的关键

## 策略参数化

- 每当你有一个有用的算法，你最终都会希望通过“策略”将其参数化。
  - 例如，我们需要按比较标准对 sort 进行参数化

```
struct Record {
  string name;      // standard string for ease of use
  char addr[24];    // old C-style string to match database layout
  // ...
};

vector<Record> vr;
// ...
sort(vr.begin(), vr.end(), Cmp_by_name());    // sort by name
sort(vr.begin(), vr.end(), Cmp_by_addr());    // sort by addr
```

## 比较

```cpp
// Different comparisons for Rec objects:

struct Cmp_by_name {
    bool operator()(const Rec& a, const Rec& b) const
        { return a.name < b.name; }        // look at the name field of Rec
};

struct Cmp_by_addr {
    bool operator()(const Rec& a, const Rec& b) const
        { return 0 < strncmp(a.addr, b.addr, 24); }        // correct?
};

// note how the comparison function objects are used to hide ugly
// and error-prone code
```

## vector

```
template<class T> class vector {
    T* elements;
    // ...
    typedef ??? iterator; // the type of an iterator is implementation defined
    // and it (usefully) varies (e.g. range checked iterators)
    // a vector iterator could be a pointer to an element

    typedef ??? const_iterator;

    iterator begin();                // points to first element
    const_iterator begin() const;
    iterator end();                  // points one beyond the last element
    const_iterator end() const;

    iterator erase(iterator p);      // remove element pointed to by p
    iterator insert(iterator p, const T& v); // insert a new element v before p
};
```

## 从 vector 中 erase()

```
p = v.erase(p); // leaves p pointing at the element after the erased one
```

- 当你 insert() 或 erase() 时，vector 的元素会移动
- 指向 vector 的迭代器会因 insert() 和 erase() 而失效

![](img/af430dff16b82a0fe61ce7dee05dcf9c_173_0.png)

