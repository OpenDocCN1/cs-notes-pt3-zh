
# C++编程(14)

唐晓晟
北京邮电大学电信工程学院

## 第16章 库组织和容器

- 标准库的设计
- 容器设计
- 向量
- 忠告

## 16.1 标准库的设计

### C++标准库

- 提供了对一些语言特征的支持，例如，存储管理
- 提供了有关实现所确定的语言方面的一些信息，例如最大的float值
- 提供了那些无法在每个系统上由语言本身做出最优化的实现函数，例如sqrt()
- 提供了一些基本的功能，使程序员可以为可移植性而依赖它们，例如，列表、映射
- 提供了一个为扩展它所提供功能的基本框架
- 为其它库提供一个公用的基础

### 16.1.1 设计约束

- 标准库所扮演的角色为它的设计提出了许多约束
- 对于每个学生，每个专业程序员，包括其他库的构造者，都应该是及其宝贵而且又是能够承担的
- 被每个程序员、在与库相关的领域中的每项工作中直接或者间接地使用
- 足够高效，能够在其他库的实现中成为手工编写的函数、类或模板的真正替代品

## 标准库组织

| Algorithms |  |
|---|---|
| `<algorithm>` | general algorithms — Chapter 18 |
| `<cstdlib>` | basearch (`qsort`) — §18.11 |

本章中的通用算法可以使用任意具有相同有效类型的元素的序列。C++ 标准库中定义的 qsort() 和 qsort() 代码用于任何类型为元素的内部数据，条件是该元素类型没有用户定义的复制构造函数和析构函数。

| Diagnostics |  |
|---|---|
| `<exception>` | exception class — §14.10 |
| `<stdexcept>` | standard exceptions — §14.10 |
| `<cassert>` | assert macro — §24.3.7.2 |
| `<cerrno>` | C-style error handling — §20.4.1 |

## 标准库组织

| Strings |  |
|---|---|
| `<string>` | string of T — Chapter 20 |
| `<cctype>` | character classification — §20.4.2 |
| `<cwtype>` | wide-character classification — §20.4.2 |
| `<cstring>` | C-style string functions — §20.4.1 |
| `<cwchar>` | C-style wide-character string functions — §20.4 |
| `<cstdlib>` | C-style string functions — §20.4.1 |

- 头文件 `<cstring>` 里声明了 `strlen()`、`strcpy()` 等一系列函数，`<cstdlib>` 里声明了 `atof()` 和 `atoi()`，它们用于将 C 风格的字符串转换成数值。

## 标准库组织

| Input/Output |  |
|---|---|
| `<iosfwd>` | forward declarations of I/O facilities — §21.1 |
| `<iostream>` | standard iostream objects and operations — §21.2.1 |
| `<ios>` | iostream bases — §21.2.1 |
| `<streambuf>` | stream buffer — §21.6 |
| `<istream>` | input stream template — §21.3.1 |
| `<ostream>` | output stream template — §21.3.1 |
| `<iomanip>` | manipulators — §21.4.6.2 |
| `<sstream>` | streams from strings — §21.5.3 |
| `<cstdlib>` | character classification functions — §20.4.2 |
| `<fstream>` | streams from/to files — §21.5.1 |
| `<cstdio>` | `printf()` family of I/O — §21.8 |
| `<cwwchar>` | `printf()` C-style I/O of wide characters — §21.8 |

## 标准库组织

| Localization |  |
|---|---|
| `<locale>` | represent cultural differences — §21.7 |
| `<clocale>` | represent cultural differences C-style — §21.7 |

- 一个 locale 使一些特征本地化，如日期的输出格式，用于表示现今的字符、字符串的排列准则，这些特征体现了不同自然语言和文化之间的差异。

## 标准库组织

| Language Support | | |
|---|---|---|
| <limits> | numeric limits | §22.5 |
| <climits> | C-style numeric scalar-limit macros | §22.1 |
| <cfloat> | C-style numeric floating-point limit macros | §22.1 |
| <new> | dynamic memory management | §16.1.3 |
| <typeinfo> | run-time type identification support | §15.4.1 |
| <exception> | exception-handling support | §14.10 |
| <cstddef> | C library language support | §6.2.1 |
| <stdarg> | variable-length function argument lists | §18.6 |
| <cstdlib> | C-style stack unwinding | §18.7 |
| <cstdarg> | program termination | §9.4.1.1 |
| <ctime> | system clock | §18.7 |
| <csignal> | C-style signal handling | §18.7 |

□ <cstddef> 定义了文件大小的size_t和size_t_t，指针类型的ptrdiff_t，以及NULL宏

## 标准库组织

| Numerics | | |
|---|---|---|
| <complex> | complex numbers and operations | §22.5 |
| <valarray> | numeric vectors and operations | §22.4 |
| <numeric> | generalized numeric operations | §22.6 |
| <cmath> | standard mathematical functions | §22.3 |
| <cstdlib> | C-style random numbers | §22.7 |

□ 由于历史的原因，abs()、fabs()和div()位于<cstdlib>里，而不是与其他数学函数一起在<cmath>里

## 标准库组织

- 用户或者库的实现者都不允许在标准头文件里添加或者减去任何东西。试图通过在包含头文件之前定义一些宏的方式去修改头文件的内容，或者通过在其环境中写声明去改变头文件里的声明意义，都是不可接受的
- 为了使用标准库的功能，必须包含有关头文件

## 16.2 容器设计

- 容器就是能保存其他对象的对象，例如：表、向量和关联数据
- C++标准库容器的设计依据的是两条准则：在各个容器的设计中提供尽可能大的自由度，同时，又使各种容器能够用用户呈现出一个公共的界面，这样将容器实现能达到最佳的效率，也使用户能写出不依赖于所使用的特定容器类型的代码

## 16.2.1 专门化的容器和迭代器

要提供向量和表，最显式方式就是对它们中的每个都按照理想的方式给予定义：

```
template<class T>class Vector{
public:
    explicit Vector(size_t n);
    T& operator[](size_t i);
};
template<class T>class List{
public:
    class Link{...};
    List();
    void put(T*);
    T* get();
};
```

每个元素都...操作。
对于每个操作，这些结构
操作上是相同的，
但我们可能每个
类提供不同的实现
而这些实现通常是
容易的。
有现成的实现版本上
是裁减的

## 专门化的容器和迭代器

对于大部分容器，一种公共的使用方式就是迭代式地穿越整个容器，一个接一个地查看元素，这通常可以通过定义适合于容器类型的迭代器类做到

最理想的情况是：一个迭代类能够应用于各种容器类

```
template<class T>class Itor { // 公共界面
public:
    virtual T* first() = 0; // 返回第一个元素指针
    virtual T* next() = 0; // 返回下一个元素指针
};
```

## 专门化的容器和迭代器

现在可以为Vector和List提供迭代器

```
template<class T>class Vector_itor:public Itor<T>{
    Vector<T>& v;
    size_t index;
public:
    Vector_itor(Vector<T>& v):v(v),index(0){}
    T* first(){ return (v.size())? &v[index=0]:0; }
    T* next(){ return (++index<v.size())? &v[index]:0; }
};
template<class T>class List_itor:public Itor<T>{
    List<T>& lst;
    List<T>::Link* p;
public:
    List_itor(List<T>& lst):lst(lst){
    }
    T* first(){ T* next(); }
};
```

## 专门化的容器和迭代器

写容器上迭代的代码

```
int count(Tor<char>& s, char term)
{
    int c = 0;
    for(char* p = ii.first(); p; p=ii.next()) if(*p==term) c++;
    return c;
}
```

注意，这种方式引起了一次虚函数的调用，很糟糕下，这种额外开销是无关大局的，但是这种方式对于标量不合适

本例中，Itor 甚至可以在Vector和List设计和实现很久以后才提供
