
- 模板定义
  - 定义函数模板
  - 定义类模板
  - 模板形参
  - 模板类型形参
  - 非类型模板形参
  - 编写泛型程序
- 实例化
  - 模板实参推断
  - 函数模板的显式实参指定

- 模板是创建类或函数的蓝图
  - 标准库定义了一个类模板，该模板定义了 `vector` 的含义
  - 它可以用于产生任意数量的特定类型的 `vector`
    - `vector<int>`
    - `vector<string>`

## 定义函数模板

- 除了形参类型不同，两个函数完全一样
  - 为每种需要比较的类型都编写重复的函数体会显得很麻烦
- 而且，如果事先不知道函数要作用于哪些类型
  - 函数有可能会作用于未知类型
  - 重复函数体的策略就不适合了
- 此时，可以定义函数模板 function template

- 模板形参表
  - 表示在函数中可以使用的类型或值
  - `compare` 函数声明了名为 `T` 的类型形参
  - `compare` 内部可以使用 `T` 引用一个类型
  - `T` 表示哪个实际类型由编译器根据所用的函数确定

- 使用函数模板时
  - 编译器会推断哪个模板实参绑定到模板形参
  - 一旦编译器确定了实际的模板实参，就称它实例化了函数模板的一个实例
  - 编译器使用实参代替形参产生并编译该版本的函数
  - 编译器为使用的每种类型编写函数

## 定义类模板

- Queue 类

```cpp
template <class Type> class Queue {
public:
    Queue();
    Type &front();
    const Type &front() const;
    void push(const Type &);
    bool empty() const;
private:
    // ...
};
```

## Const的用法

- 2. 用 `const` 修饰函数的返回值
- 该返回值只能被赋给加 `const` 修饰的同类型指针
- 例如函数
- `const char * GetString(void);`
- 如下语句将出现编译错误：
- `char *str = GetString(); //error`
- 正确的用法是
- `const char *str = GetString();`
- 如果函数返回值采用“值传递方式”，由于函数会把返回值复制到外部临时的存储单元中，加 `const` 修饰没有任何价值

- 3. `const` 成员函数
- 任何不会修改数据成员的函数都应该声明为 `const` 类型
- 如果在编写 `const` 成员函数时，不慎修改了数据成员，或者调用了其它非 `const` 成员函数，编译器将指出错误，这无疑会提高程序的健壮性
- `const` 成员函数的声明看起来怪怪的：`const` 关键字只能放在函数声明的尾部，大概是因为其它地方都已经被占用了

## 定义类模板

- 类模板也是模板
  - 以 `template` 开头
  - 后接模板形参表
- 在使用类模板时，必须为模板形参显式指定实参

```cpp
Queue<int> qi;
Queue<vector<double>> qc;
Queue<string> qs;
```

- 编译器使用实参来实例化这个类的特定类型版本
  - 编译器用用户提供的实际特定类型代替 `Type`，重新编写 `Queue` 类

## 模板形参

- 模板形参的名字没有本质含义
  - 如果是类型形参，则表示未知类型
  - 如果是非类型形参，则表示是未知值

```cpp
template <typename Glorp>
int compare(const Glorp &v1, const Glorp &v2)
{
    if (v1 < v2) return -1;
    if (v2 < v1) return 1;
    return 0;
}
```

- 模板形参的名字可以
  - 在声明为模板形参之后
  - 直到模板声明或定义的末尾处使用
- 模板形参遵循常规的名字屏蔽规则

```cpp
typedef double T;

template <class T> T calc(const T &a, const T &b)
{
    T tmp = a; // which T ?!
    return tmp;
}
```

- 将 `T` 定义为 `double` 的全局类型别名，被命名为 `T` 的类型形参所屏蔽
- 用作模板形参的名字不能在模板内部重用：

```cpp
template <class T> T calc(const T &a, const T &b)
{
    typedef double T;
    T tmp = a;
    return tmp;
}
```

- 模板形参的名字只能在同一个模板形参中使用一次

```cpp
template <class V, class V> V calc(const V&, const V&);
```

- 模板形参的名字可以在不同的模板中重用

```cpp
template <class T> T calc(const T&, const T&);
template <class T> int compare(const T&, const T&);
```

- 模板可以只声明不定义
  - `template <class T> int compare(const T&, const T&);`
- 同一模板的声明和定义中，模板形参的名字不必相同
  - `template <class T> T calc(const T&, const T&);`
  - `template <class U> U calc(const U&, const U&){ ... };`
- 每个模板类型形参前面必须带上关键字 `class` 或 `typename`
- 每个非类型形参前面必须带上类型名字
- 省略关键字或类型说明符都是错误的
  - `template <class T, U> T calc(const T&, const U&);`

### 模板类型形参

- 由关键字 `class` 或 `typename` 后接说明符构成
- 模板类型形参可以作为类型说明符用在模板中任何地方
- `typename` 和 `class` 具有相同含义，可以互换使用
  - `template <typename T, class U> T calc(const T&, const U&)`
- `typename` 看起来更加直观
  - 内置类型，即非类类型，也可以作为实际的类型形参

### 模板非类型形参

- 在调用函数时，非类型形参将用值代替
- 值的类型在模板形参表中指定

```cpp
template <class T, size_t N> void array_init(T (&parm) [N])
{
    for (size_t i = 0; i != N; ++i)
        parm[i] = 0;
}
int x[42];
double y[10];
array_init(x);
array_init(y);
```

`size_t` 是无符号的整数类型，并且和操作系统无关

- 类型等价性
  - 求值结果相同的表达式被认为是等价的

```cpp
int x[42];
const int sz = 40;
int y[sz+2];
array_init(x);
array_init(y);
```
