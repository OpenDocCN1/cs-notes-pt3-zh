
## IntSet示例

- 思考：当我们新创建一个整数集时
  IntSet s;
- s的数据成员还没有初始化
- 这意味着numElts可以是任何值
  - 但是表示不变式规定它现在必须是0！
- 因此，必须定义一个特殊的成员函数，称为“构造函数 (constructor)”
- 构造函数(实际上是缺省构造函数)具有下面的签名：
  IntSet(); // EFFECTS: creates an empty IntSet

```
const int MAXELTS = 100;
class IntSet { // OVERVIEW: a mutable set of integers, |set| <= MAXELTS
    int elts[MAXELTS];
    int numElts;
    int indexOf(int v);
    public:
    IntSet();          // EFFECTS: creates an empty IntSet
    void insert(int v);  // MODIFIES: this, EFFECTS: this = this + {v}
    void remove(int v); // this=this-{v} if v is in this; throws int v otherwise.
    bool query(int v);   // EFFECTS: returns true if v is in this, false otherwise
    int size();          // EFFECTS: returns |this|
}
```

## IntSet示例

- 这个函数没有任何返回类型，因为它不需要返回任何值
- 在这个例子中，它也没有参数
- 但是可以保证它是第一个被调用的函数
  - 在创建对象后立即被调用
  - 并且向其提供了未初始化的IntSet
  - 用于向其中构建符合表达式不变式的IntSet
- 下面是构造器代码：

```cpp
IntSet::IntSet(): numElts(0)
{
}
```

- 这种语法被成为“初始化语法(initialization syntax)”

- 我们也可以按照下面的方式编写构造函数：
```cpp
IntSet::IntSet()
{
    numElts = 0;
}
```
- 但是，这种方式被认为不符合C++编程惯例

## IntSet示例

- 这个类展示了聚集的优点：
  - 如果我们要将一个数组传递到函数中
  - 就必须传递数组以及在数组中的元素个数
  `void add_one (int a[], int elts);`
- 这使得代码编写工作量增加了
- 而且如果传递的elts值有误，则会产生危害
  - 数组访问越界

## IntSet示例

- 通过聚集成类，我们可以编写下面的函数

`void add_one (IntSet& set);`

- 这使得代码的编写更加简单
  - 我们不用担心计数值与数组互相分离了

## 圆点操作符与作用域解析操作符

- 用于指定成员
- 圆点操作符：
  - 指定特定对象的成员
  - 与struct相同
- 作用域解析操作符：
  - 指定函数定义出自哪个类

## 类的地位

- 类是“全能类型 (full-fledged type)”
  - 就像 int 和 double 等数据类型
- 变量可以具有 class 类型
  - 我们称其为对象 (object)
- 参数也可以具有 class 类型
  - 按值传递
  - 按引用传递

- 可以像使用其他任何类型一样使用 class 类型

- 任何数据类型都包括：
  - 数据 (数据的范围)
  - 操作 (可以在数据上执行的操作)
- 例如： int 数据类型具有
  - 数据: - 2³²- + 2³²-1
  - 操作: +, -, *, /, %, 逻辑运算, etc.
- 与类相同
  - 类是由类的定义者指定数据以及在数据上允许的操作

## 面向对象编程（OOP）原则

- 信息隐藏
  - 操作的细节对类的用户来说是不了解的
- 数据抽象
  - 数据如何组装到类中对用户来说是不了解的
- 封装
  - 将数据与操作群组在一起，同时将细节隐藏

- 类中的数据总是指派为类定义内私有！
  - 维护了OOP的原则
  - 向用户隐藏了数据
  - 只允许通过操作来处理数据
    - 即通过成员函数来处理数据

- 公有项(通常是成员函数)是用户可访问的(user-accessible)

## 私有与公有实例

- 修改关于日期的类:
```cpp
class DayOfYear {
    public:
        void input();
        void output();
    private:
        int month;
        int day;
};
```
- 数据现在是私有的
- 对象不能直接访问数据

## 私有与公有实例

- 假设对于前面的示例，声明变量：
DayOfYear today;

- 对象 today 只能访问 公有成员
cin >> today.month; // NOT ALLOWED!
cout << today.day; // NOT ALLOWED!

## 私有与公有实例

- 取而代之的是，必须调用公有操作
today.input();
today.output();
- 执行方法的过程与执行函数一样：
  - 计算传入参数
  - 创建内存帧
  - 传递传入参数
  - 执行函数
  - 销毁内存帧

## 私有与公有风格

- 可以混合使用公有与私有成员
- 通常先声明 public 成员
  - 给使用该类的程序员一个清晰的视图，说明他可以 “用” 什么
  - private 数据是 “隐藏” 起来的，因此与用户无关
- 在类定义的外部，不能改变（甚至不能访问） private 数据

## 访问器和修改器函数

- 用户需要使用对象的数据执行处理
- 调用访问器(accessor)成员函数
  - 允许读取对象的数据
  - 也被称为 “getter” 成员函数
  - 执行对成员数据的获取操作
- 调用修改器(Mutator)成员函数
  - 允许修改对象的数据
  - 基于不同的应用执行不同的操作
  - 也被称为 “setter” 成员函数

## 分离接口与实现

- 类的用户不需要知道类的实现细节
  - OOP原则 → 封装
- 用户只需要 “规则”
  - 称为类的接口(interface)
  - 在C++ 中是 public 成员函数与相关的注释
- 类的实现被隐藏
  - 成员函数的定义在其他地方
  - 用户不需要看到它们

## 类的优点

- 聚集的优点
`void add_one (int a[], int elts);`
  - 丑陋!
  - 危险： elts值有误怎么办?
`void add_one (IntSet& set);`
  - 计数值和数组不再分离
  - 隐藏了集的表示

## 结构与类

- 结构是不同类型的数据集合
- 类用来将数据和函数组合到单个单元中 → 对象 object
- 成员变量和成员函数
  - 可以是公有的 → 可以在类的外部被访问
  - 可以是私有的 → 只能在成员函数的定义内被访问
- 类和结构类型都可以是函数的形参
