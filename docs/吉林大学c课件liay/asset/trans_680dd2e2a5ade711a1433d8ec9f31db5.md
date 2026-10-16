

## 模板&类

通过特化类模板，你可以优化基于某种特定类型的实现，或者克服某种特定类型在实例化类模板时所出现的不足。

进行类模板的特化时，每个成员函数都必须重新定义为普通函数，原来模板函数中的每个 `T` 也相应地被进行特化的类型取代：

// 特化

// 例子（下）

```cpp
void main(){
    List<int> i;
    i.Set(1);
    cout << i.Get() << endl;
    List<double> k;
    k.Set(1);
    cout << k.Get() << endl;
    k.print();
}
```

// 注意多个类型参数情况

// 特化其中一部分类型参数为确定的类型，称为局部特化

```cpp
template <typename T1, typename T2>
class A
{......};
```

```cpp
template <typename T>
class A<T,T>{....};  // 仍为类模板
```

```cpp
template <typename T>
class A<T,Cat>
{......};
```

使用时：

```cpp
A<int,Cat> aa1;
```

```cpp
A<int,int> aa2;
```

```cpp
A<Cat,Cat> aa3; // error
```

包含：
一般的办法是将（函数、类）模板的整个定义都放在头文件中。

```cpp
// List.h
template<typename T>
class List {
public:
    void Set(T);
    T Get();
private:
    T i;
};

template<typename T>
void List<T>::Set(T k){ i = k; }

template<typename T>
T List<T>::Get(){ return(i); }
```

```cpp
// main.cpp
#include "List.h"
void main(){
    List<double> k;
    k.Set(1);
    cout << k.Get() << endl;
}
```

## 模板&类

// 分离（多文件机制）

// 例子

List.h:

```cpp
template<typename T>
class List {
public:
    void Set(T);
    T Get();
private:
    T i;
};
```

List.cpp:

```cpp
#include "List.h"
template<typename U>
void List<U>::Set(U k){ i = k; }
template<typename T>
T List<T>::Get(){ return(i); }
```

main.cpp:

```cpp
#include "List.h"
void main(){
    List<double> k;
    k.Set(1);
    cout << k.Get() << endl;
}
```

// template 前加上 export

- 模板可以有层次，一个模板可以作为基类，派生出派生模板类。

《C++ Templates》

```c
float a = 5;
printf("%d", a);
```

`%d` 格式不能正常处理数据输出；

```cpp
class aa {
public:
    int a;
    int b;
};

aa a;
a.a = 1;
a.b = 2;
printf("%?", a);
```

不能直接输出类的对象内容。

![](img/2a27c9e9d8641bba50c8f3e0109e4e84_338_0.png)

## I/O 流

“流”就是“流动”，是物质从一处向另一处流动的过程。

C++ 流是指信息从外部输入设备（如键盘和磁盘）向计算机内部（即内存）输入和从内存向外部输出设备（如显示器和磁盘）输出的过程，这种输入输出过程被形象地比喻为“流”。

为了实现信息的内外流动，C++ 系统定义了 I/O（流）类库（带有面向对象的输入/输出软件包），其中的每一个类都称作相应的流或流类，用以完成某一方面的功能。

根据一个流类定义的对象也时常被称为流，每一个流类对象称为一个数据流，在内存中为每一个数据流开辟一个内存缓冲区，用来存放流中的数据。

凡是数据从一个地方传输到另一个地方的操作都是流的操作。因此一般意义下的读操作（输入）在流数据抽象中被称为（从流中）提取，写操作（输出）被称为（向流中）插入。

C++ 语言系统为实现数据的输入和输出定义了一个庞大的类库，它包括的类主要有：

- `ios`：抽象基类
- `iostream`：输入流类 `istream`，输出流类 `ostream`，输入输出流类 `iostream`
- `fstream`：输入文件流类 `ifstream`，输出文件流类 `ofstream`，输入输出文件流类 `fstream`
- `strstream`：输入字符串流类 `istrstream`，输出字符串流类 `ostrstream`，输入输出字符串流类 `strstream`

## ios 类的派生关系

```text
ios
istream
fstreambase
strstreambase
ostream
ifstream
istrstream
ofstream
ostrstream
iostream
fstream
strstream
istream_withassign
iostream_withassign
ostream_withassign
```

## 标准 I/O

C++ 不仅定义有现成的 I/O 类库供用户使用，而且还为了用户进行标准 I/O 操作，在 `iostream`（输入、输出类的头文件）中定义了四个全局对象，它们分别是 `cin`、`cout`、`cerr` 和 `clog`。

```cpp
ostream cout;  // 标准输出流，默认屏幕，可以重定向
istream cin;   // 标准输入流，默认键盘
ostream cerr;  // 标准错误流，默认屏幕，不能重定向，不经过缓冲区
ostream clog;  // 标准错误流，默认屏幕（与 cerr 唯一区别就是经过缓冲区）
```

C++ 为 `cout` 流对象开辟一个缓冲区：

```cpp
cout << "c++" << 10 << 2.5 << endl;
ostream &operator<<(ostream &out, char *p);
ostream &operator<<(ostream &out, int p);
ostream &operator<<(ostream &out, char p);
ostream &operator<<(ostream &out, float p);
```

## I/O 类

```cpp
#include <iostream>
using namespace std;

class aa {
    float a;  float b;
public:
    float &aaa() { return(a); }
    float &bbb() { return(b); }
};

ostream &operator<<(ostream &out, aa &a) {
    out << a.aaa() << a.bbb() << endl;
    return(out);
}

void main() {
    aa a;
    a.aaa() = 1; a.bbb() = 2;
    cout << a;
}
```

## 输出输入

```cpp
// 格式输出
#include <iostream>
#include <iomanip>
using namespace std;

void main() {
    double a = 0.12345;
    cout.precision(2);
    cout << a << endl;

    cout << a << setprecision(3) << a << endl;
    cout << a << endl;
}
```

成员函数　　控制符号

## 输出输入

```cpp
#include <iostream>
using namespace std;

void main() {
    char a[20];
    cin >> a;
    cout << a << endl;

    cin.getline(a, 11, 'a');
    cout << endl << a;
}
```

运行程序结果：

He told me a news
He

told me

输入数据按回车键后，数据才被送入键盘缓冲区，形成输入流。`istream` 流类成员函数的使用可以更加精细地控制输入。

## 文件流类

文件的概念：存储在外部介质上的数据集合。

两类：程序文件和数据文件。

程序中输入输出的对象是数据文件。

数据文件的组织形式分为：ASCII 文件和二进制文件。

ASCII 文件（文本文件或字符文件）：每一个字节放一个 ASCII 代码，代表一个字符。可直接显示或打印。

二进制文件（内部文件或字节文件）：把内存中的数据按其在内存中的存储形式原样输出到磁盘上保存。

对于字符信息二者是一样的，数值数据二者是不同的。

