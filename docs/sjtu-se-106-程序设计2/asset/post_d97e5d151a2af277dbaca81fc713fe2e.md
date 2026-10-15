
![](img/af430dff16b82a0fe61ce7dee05dcf9c_174_0.png)

## list

```
template<class T> class list {
    Link* elements;
    // ...
    typedef ??? iterator;  // the type of an iterator is implementation defined
                           // and it (usefully) varies (e.g. range checked iterators)
                           // a list iterator could be a pointer to a link node
    typedef ??? const_iterator;

    iterator begin();                 // points to first element
    const_iterator begin() const;
    iterator end();                   // points one beyond the last element
    const_iterator end() const;

    iterator erase(iterator p);       // remove element pointed to by p
    iterator insert(iterator p, const T& v); // insert a new element v before p
};
```

## insert() into list

```
list<int>::iterator p = v.begin(); ++p; ++p; ++p;
list<int>::iterator q = p; ++q;
```

```
v = v.insert(p,99);    // leaves p pointing at the inserted element
```

- Note: q is unaffected
- Note: No elements moved around

## erase() from list

```
p = v.erase(p);  // leaves p pointing at the element after the erased one
```

- Note: list elements do not move when you insert() or erase()

![](img/af430dff16b82a0fe61ce7dee05dcf9c_176_0.png)

![](img/af430dff16b82a0fe61ce7dee05dcf9c_176_1.png)

## Ways of traversing a vector

```
```cpp
for(int i = 0; i<v.size(); ++i)              // why int?
    ...  // do something with v[i]

for(vector<int>::size_type i = 0; i<v.size(); ++i)    // longer but always correct
    ...  // do something with v[i]

for(vector<int>::iterator p = v.begin(); p!=v.end(); ++p)
    ...  // do something with *p
```
```

- know both ways (iterator and subscript)
  - The subscript style is used in essentially every language
  - The iterator style is used in C (pointers only) and C++
  - The iterator style is used for standard library algorithms
  - The subscript style doesn’t work for lists (in C++ and in most languages)
- use either way for vectors
  - There are no fundamental advantage of one style over the other
  - But the iterator style works for all sequences
  - Prefer `size_type` over plain `int`
    - pedantic, but quiets compiler and prevents rare errors

## Some useful standard headers

- `<iostream>` I/O streams, cout, cin, ...
- `<fstream>` file streams
- `<algorithm>` sort, copy, ...
- `<numeric>` accumulate, inner_product, ...
- `<functional>` function objects
- `<string>`
- `<vector>`
- `<map>`
- `<list>`
- `<set>`

## 主要内容

- 泛型程序设计
- 迭代器
- 顺序容器
- 关联容器
- 函数对象
- 算法
- 深度探索

## 泛型程序设计

- 编写不依赖于具体数据类型的程序
- 将算法从特定的数据结构中抽象出来，成为通用的
- C++的模板为泛型程序设计奠定了关键的基础
- 几个术语
  - 概念（concept）：用来界定具备一定功能的数据类型，如“支持 `<` 运算符”的数据类型构成Comparable这一概念；
  - 模型（model）：符合一个概念的数据类型称为该概念的模型，如int型是Comparable概念的模型。

![](img/af430dff16b82a0fe61ce7dee05dcf9c_182_0.png)

## STL程序实例(例10-1)

```
```cpp
//包含的头文件略去……
using namespace std;
int main() {
    const int N = 5;
    vector<int> s(N);
    for (int i = 0; i < N; i++)
        cin >> s[i];
    transform(s.begin(), s.end(),
              ostream_iterator<int>(cout, " "), negate<int>());
    cout << endl;
    return 0;
}
```
```

![](img/af430dff16b82a0fe61ce7dee05dcf9c_183_0.png)

## STL的组成部分

STL是泛型程序设计的一个范例

- 容器（container）
- 迭代器（iterator）
- 算法（algorithms）
- 函数对象（function object）

泛型程序设计

![](img/af430dff16b82a0fe61ce7dee05dcf9c_184_0.png)

## 输入流迭代器和输出流迭代器

- 输入流迭代器
  - istream_iterator<T>
  - 以输入流（如cin）为参数构造
  - 可用*(p++)获得下一个输入的元素
- 输出流迭代器
  - ostream_iterator<T>
  - 构造时需要提供输出流（如cout）
  - 可用(*p++) = x将x输出到输出流
- 二者都属于适配器
  - 适配器是用来为已有对象提供新的接口的对象
  - 输入流适配器和输出流适配器为流对象提供了迭代器的接口

迭代器

## 例10-2

迭代器

```
//包含的头文件略去……
using namespace std;
double square(double x) {
    return x * x;
}
int main() {
    transform(istream_iterator<double>(cin),
        istream_iterator<double>(),
        ostream_iterator<double>(cout, "\t"), square);
    cout << endl;
    return 0;
}
```
