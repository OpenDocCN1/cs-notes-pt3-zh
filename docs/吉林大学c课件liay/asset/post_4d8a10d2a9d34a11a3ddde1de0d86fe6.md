

## 模板的参数是非类型参数（表达式形参）

```cpp
template <class T, int i>
int find(T a[], T k)
{
    for (int j = 0; j < i; j++)
        if (a[j] == k)
            return j;
    return -1;
}

void main()
{
    int a[10] = {0};
    cout << find<int, 10>(a, 1);
}
```

### 非类型参数

模板非类型参数：则形参的类型是某种具体的数据类型。

模板非类型参数表示该参数名代表了一个潜在的值，而该值代表了模板定义中的一个常量。

模板非类型参数被用作一个常量值出现在模板定义的余下部分。它可以用在要求常量的地方，如数组声明中指定数组的大小或作为枚举常量的初始值。

## 第一次上机：

写程序验证如下内容：

- 浅拷贝仅能简单复制指针的值；
- 全局对象、静态成员的构造函数在 main 函数之前执行；
- 构造函数可以实现类型转换；
- 堆空间生命周期与申请函数不同步；

## 第二次上机：

1. 编写运算符重载函数程序。
2. 编写程序验证继承的权限变化。
3. 编写程序验证多态，分别通过指针、引用和成员函数的方式。

## 第三次上机：

1. 编写程序定制类模板，并写出测试程序。
2. 写程序，实现文件 I/O 以及字符串 I/O 的操作。
3. 写程序验证使用 C++ 异常机制，当异常被捕获时，对已经使用到的资源回收。

## 8-2：类模板

```cpp
// 栈类
class NODE {
public:
    int age;
    NODE* next;
};

class Stack {
public:
    Stack() { head = 0; }
    void push(NODE&);
    NODE pop();
private:
    NODE* head;
};

void Stack::push(NODE& i) {
    NODE* p = new NODE;
    *p = i;
    p->next = head;
    head = p;
}

NODE Stack::pop() {
    NODE p = *head;
    NODE* q = head;
    head = head->next;
    delete q;
    return p;
}

void main() {
    Stack i;
    NODE s, t;
    s.age = 20; t.age = 22;
    i.push(s);
    i.push(t);
    cout << (i.pop()).age;
    cout << (i.pop()).age;
}
```

## 模板&类

```cpp
template <typename T>
class Stack {
public:
    void push(T);
    T pop();
private:
    T* head;
};

template <typename T>
void Stack<T>::push(T i) {
    T* p = new T;
    *p = i;
    p->next = head;
    head = p;
}

template <typename T>
T Stack<T>::pop() {
    T p = *head;
    T* q = head;
    head = head->next;
    delete q;
    return p;
}
```

// 与普通类一样，类模板的成员函数也可以在类模板定义中定义具体实现，这时，该函数是内联的（inline）。

## 模板&类

```cpp
class NODE {...};
class Student {...};

void main() {
    Stack<NODE> i;    // 实例化；(只实例化模板的定义部分)
    // 隐式类型实例化可以吗？ // 类模板&模板类?
    NODE s, k;
    s.age = 20; k.age = 21;
    i.push(s);    // 第一次调用函数模板时，对其实例化
    i.push(k);    // 成员函数的模板参数由其调用对象确定
    cout << (i.pop()).age;
    Stack<Student> m;
}
```

这个类的类型是 Stack<T>，其中 T 是模板参数。因此，当在声明中需要使用该类的类型时，你必须使用 Stack<T>。例如，如果你要声明自己实现的拷贝构造函数和赋值运算符，那么应该这样编写：

```cpp
template <typename T>
class Stack {
// ....
};

Stack<T>::Stack(Stack<T> const&);    // 拷贝构造函数
Stack<T>& Stack<T>::operator=(Stack<T> const&); // 赋值运算符
// ...
```

当使用类名而不是类的类型时，就应该只用 Stack；譬如，当你指定类的名称、类的构造函数、析构函数时，就应该使用 Stack。

## 类模板中的 static 成员

类模板可以像任意其他类一样声明 static 成员。

因为每个类模板的实例化表示截然不同的类，所以每个类都有自己的 static 成员。

给定实例化的类所有对象都共享同一个 static 成员。

与任意其他成员函数一样，static 成员函数只有在程序中使用时才进行实例化。

```cpp
template <typename T>
class Stack {
    static Stack* phead;
};

template <typename T>
Stack<T>* Stack<T>::phead = 0;
```

标准 vector 是定义在名字空间 std 的一个类模板。向量对象的定义和初始化方式，就是模板的实例化的过程。

- vector<int> a(10);
- vector<int> b(10, 1);
- vector<int> c(b);
- vector<int> d(b.begin(), b.begin() + 3);

// 类模板可以有多个类型参数，如：

```cpp
template <typename T, typename U>
class List {... ...};

List<NODE, Student> k;
```

## 模板&类

```cpp
template <typename T, int Num>
class List {
public:
    void Set(T);
    T Get();
    T a[Num];
private:
    T i;
};

template <typename U, int Count>
void List<U, Count>::Set(U k) { i = k; }

template <typename T, int Count>
T List<T, Count>::Get() { return i; }

void main() {
    int x = 1, y = 2;
    List<int, 9> i;
    i.Set(1); // i.List<int, 9>::Set(1);
    cout << i.Get() << endl;
}
```

> Num 应当给出确定的参数值
> 注意 U 和 Count

## 模板&类

```cpp
// 栈
template <typename T = NODE>
class Stack {
public:
    void push(T);
    T pop();
private:
    T* head;
};

template <typename T>
void Stack<T>::push(T i) { .... .... }

template <typename T>
T Stack<T>::pop() { .... .... }

Stack<> object;
stack<Student> object2;
```

// 类模板也允许默认参数

## 模板&类

// 定做（Specialization）定制、特化、专门化
// 例子（上）

```cpp
template <typename T>
class List {
public:
    void Set(T);
    T Get();
private:
    T i;
};

template <typename T>
void List<T>::Set(T k) { i = k; }

template <typename T>
T List<T>::Get() { return i; }
```

```cpp
template <>
class List<double> {
public:
    void Set(double);
    double Get();
    void print();
private:
    double i;
    int m;
}; // 一个普通类
```

```cpp
void List<double>::Set(double k) { i = k + 1; }

double List<double>::Get() { return -1 * i; }

void List<double>::print() {
    cout << i << endl;
}
```

// 普通的函数

