

## IntSet 示例

- 思考：当我们新创建一个整数集时  
  `IntSet s;`
- `s` 的数据成员还没有初始化
- 这意味着 `numElts` 可以是任何值
  - 但是表示不变式规定它现在必须是 `0`！
- 因此，必须定义一个特殊的成员函数，称为“构造函数（constructor）”
- 构造函数（实际上是默认构造函数）具有下面的签名：  
  `IntSet(); // EFFECTS: creates an empty IntSet`

```cpp
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

## IntSet 示例

- 这个函数没有任何返回类型，因为它不需要返回任何值
- 在这个例子中，它也没有参数
- 但是可以保证它是第一个被调用的函数
  - 在创建对象后立即被调用
  - 并且向其提供了未初始化的 `IntSet`
  - 用于构建一个满足表示不变式的 `IntSet`
- 下面是构造函数的代码：

```cpp
IntSet::IntSet(): numElts(0)
{
}
```

- 这种语法被称为“初始化语法（initialization syntax）”

- 我们也可以按照下面的方式编写构造函数：
```cpp
IntSet::IntSet()
{
    numElts = 0;
}
```
- 但是，这种方式被认为不符合 C++ 编程惯例

## IntSet 示例

- 这个类展示了聚合的优点：
  - 如果我们要将一个数组传递给函数
  - 就必须同时传递数组以及数组中的元素个数  
  `void add_one (int a[], int elts);`
- 这使得代码编写的工作量增加了
- 而且如果传递的 `elts` 值有误，则会产生危害
  - 数组访问越界

## IntSet 示例

- 通过将数据聚合到类中，我们可以编写下面的函数：

`void add_one (IntSet& set);`

- 这使得代码编写更加简单
  - 我们不用担心计数值与数组彼此分离了

## 圆点操作符与作用域解析操作符

- 用于指定成员
- 圆点操作符：
  - 指定特定对象的成员
  - 与 `struct` 中的用法相同
- 作用域解析操作符：
  - 指定函数定义出自哪个类

## 类的地位

- 类是“完整类型（full-fledged type）”
  - 就像 `int` 和 `double` 等数据类型
- 变量可以具有 `class` 类型
  - 我们称其为对象（object）
- 参数也可以具有 `class` 类型
  - 按值传递
  - 按引用传递

- 可以像使用其他任何类型一样使用 `class` 类型

- 任何数据类型都包括：
  - 数据（数据的范围）
  - 操作（可以在数据上执行的操作）
- 例如：`int` 数据类型具有
  - 数据：`-2³¹` 到 `2³¹-1`
  - 操作：`+`、`-`、`*`、`/`、`%`、逻辑运算等
- 类也是如此
  - 类由类的定义者指定数据，以及允许在数据上执行的操作

## 面向对象编程（OOP）原则

- 信息隐藏
  - 操作的细节对类的用户来说是不可见的
- 数据抽象
  - 数据如何组装到类中对用户来说是不可见的
- 封装
  - 将数据与操作组合在一起，同时隐藏实现细节

- 类中的数据通常被声明为类定义内的私有成员！
  - 维护了 OOP 的原则
  - 向用户隐藏了数据
  - 只允许通过操作来处理数据
    - 即通过成员函数来处理数据

- 公有成员（通常是成员函数）是用户可访问的（user-accessible）

## 私有与公有实例

- 修改关于日期的类：
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
  `DayOfYear today;`

- 对象 `today` 只能访问公有成员  
  `cin >> today.month; // NOT ALLOWED!`  
  `cout << today.day; // NOT ALLOWED!`

## 私有与公有实例

- 取而代之的是，必须调用公有操作：  
  `today.input();`  
  `today.output();`
- 执行方法的过程与执行函数一样：
  - 计算传入参数
  - 创建内存帧
  - 传递传入参数
  - 执行函数
  - 销毁内存帧

## 私有与公有风格

- 可以混合使用公有成员与私有成员
- 通常先声明 `public` 成员
  - 给使用该类的程序员一个清晰的视图，说明他可以“使用”什么
  - `private` 数据是“隐藏”的，因此与用户无关
- 在类定义的外部，不能改变（甚至不能访问）`private` 数据

## 访问器和修改器函数

- 用户需要使用对象的数据执行处理
- 调用访问器（accessor）成员函数
  - 允许读取对象的数据
  - 也被称为“getter”成员函数
  - 执行获取成员数据的操作
- 调用修改器（mutator）成员函数
  - 允许修改对象的数据
  - 根据不同的应用执行不同的操作
  - 也被称为“setter”成员函数

## 分离接口与实现

- 类的用户不需要知道类的实现细节
  - OOP 原则 → 封装
- 用户只需要“规则”
  - 称为类的接口（interface）
  - 在 C++ 中是公有成员函数与相关注释
- 类的实现被隐藏
  - 成员函数的定义位于其他地方
  - 用户不需要看到它们

## 类的优点

- 聚合的优点  
  `void add_one (int a[], int elts);`
  - 丑陋！
  - 危险：如果 `elts` 值有误怎么办？
  
  `void add_one (IntSet& set);`
  - 计数值和数组不再分离
  - 隐藏了集合的表示

## 结构与类

- 结构是不同类型的数据集合
- 类用来将数据和函数组合到单个单元中 → 对象（object）
- 成员变量和成员函数
  - 可以是公有的 → 可以在类的外部被访问
  - 可以是私有的 → 只能在成员函数的定义内被访问
- 类类型和结构类型都可以作为函数的形参

