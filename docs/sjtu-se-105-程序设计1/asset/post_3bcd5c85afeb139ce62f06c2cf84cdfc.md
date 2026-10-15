
## Figure 类:center()

- 父类Figure包含可以应用于所有图形的函数
- 考虑：
  - center():将图形移动到屏幕的中央
  - 先擦出，然后再重绘
  - 因此Figure::center() 将使用draw()来重绘
- 事情变得复杂了！
  - 应该使用哪个类的draw()函数呢？
- 虚函数可以解决这个问题
  - 目前为止，仍旧没有任何新知识点

- 考虑新增一类图形：
  - 从Figure类中导出Triangle类
- 函数center()继承自Figure
  - 它在三角形中能工作吗？
  - 它使用了draw()，而draw()对每种图形都是不一样的！
  - 它将使用Figure::draw()，而这个函数不适用于三角形
- 我们希望继承的center()函数将使用
  - Triangle::draw()而不是Figure::draw()
- 但是Triangle类编写Figure::center()的时候还不存在呢
  - Figure::center()不知道三角形的存在！

## 虚函数实例

- 汽车零配件商店的销售记录跟踪程序
  - 跟踪所有的销售情况
  - 不知道会有多少种销售方式
  - 先实现：产品按原价销售
  - 以后实现：打折销售，邮件订单等
  - 考虑价格和税等之外的因素

## 虚函数实例

- 程序必须：
  - 计算每天的总销售金额
  - 计算最大/最小销售额的日期
  - 可能需要计算日平均销售额
- 所有数据都来自一张张的账单
  - 但是许多计算账单的函数都将在“以后”添加进来
    - 当添加不同类型的销售方式时
- 因此“计算账单”的函数需要是虚函数

```
class Sale
{
    public:
        Sale();
        Sale(double thePrice);
        double getPrice() const;
        virtual double bill() const;
        double savings(const Sale& other) const;
    private:
        double price;
};
```

const means that no data member modification

## savings成员函数和 < 操作符

```
double Sale::savings(const Sale& other) const
{
    return (bill() - other.bill());
}
```

```
bool operator < (const Sale& first, const Sale& second)
{
    return (first.bill() < second.bill());
}
```

- 注意：它们都使用了成员函数bill()!

- 表示销售单件商品，没有任何额外的打折或费用
- 注意在bill成员函数的声明中使用保留词 “virtual”
- 影响：
  - Sale的导出类可以定义它们自己的bill版本
  - Sale的其他成员函数将使用导出类对象提供的bill版本
  - 它们不会自动使用Sale的版本

```
class DiscountSale : public Sale {
    public:
        DiscountSale();
        DiscountSale(double thePrice, double theDiscount);
        double getDiscount() const;
        void setDiscount(double newDiscount);
        double bill() const;
    private:
        double discount;
};
```

## DiscountSale导出类

- DiscountSale的成员bill()的实现与Sale不同
  - 特别加入了“打折”
- 成员函数savings和操作符<
  - 对DiscountSale类的所有对象都将使用bill()的这个定义
  - 而不是缺省地使用Sales类中的版本

- 回想一下在导出类DiscountSale之前编写的Sale
  - 成员savings和"<"是在没有DiscountSale之前编译的
- 但是，在像下面的调用中：
  DiscountSale d1, d2;
  d1.savings(d2);
- 在savings()中对函数bill()的调用仍旧知道应该使用来自DiscountSale类的bill()定义
- 很强大！

## 为什么不把所有方法都变成虚函数？

- 虚函数的优点已经很明显了
- 但是它也有缺点！
- 主要缺点之一：开销
  - 使用了更多的存储空间
  - 延迟绑定是 “操作中处理(on the fly)” 的，因此程序运行较慢
- 因此，虚函数如果不是必需的，则不应该使用

## 扩展类型兼容性

- 假如：
- Derived是Base的导出类
  - Derived对象可以赋值给Base类型的对象
  - 但是反之不可以！
- 考虑前面的例子：
  - DiscountSale 是一个Sale，但是反之不然

```
class Pet {
    public:
        string name;
        virtual void print() const;
};
```

```
class Dog : public Pet {
    public:
        string breed;
        virtual void print() const;
};
```

- 成员 name 和 breed 是公有的，这只是为了举例，属非典型

## 使用Pet和Dog类

- 现在假设有如下声明:
  Dog vdog;
  Pet vpet;

- 任何是狗的对象都是宠物:
  vdog.name = "Tiny";
  vdog.breed = "Great Dane";
  vpet = vdog;

- 这些语句是允许的

- 子类型可以赋值给父类型，但是反之不然
  - 宠物不都(必须)是狗

- 注意，赋值给 vpet 的对象，就丢失了其breed域：
  cout << vpet.breed;
- 这称为切片问题
- 看起来似乎是合适的
  - Dog被当做了Pet变量，因此它不应该被当做Pet
    - 因此也就不需要有 “dog” 特有的属性
- 但是对于严谨的计算机科学家来说，这么做是有问题的
  - 因为信息丢失了

## 切片问题修正

- 在C++中，切片问题是令人讨厌的
  - 它仍旧是一条纯种的狗
  - 我们希望在它被当做Pet时仍旧可以引用到其breed属性
- 有什么方法可以实现这个目的吗？
- 是的，虚函数！
- 但是如何做呢？
  - 可以将虚函数与指向动态变量的指针结合使用

## 切片问题示例

```
Pet *ppet;
Dog *pdog;
pdog = new Dog;
pdog->name = "Tiny";
pdog->breed = "Great Dane";
ppet = pdog;
```

- 不能访问ppet指针指向的对象的breed域
  cout << ppet->breed; //ILLEGAL!

## 切片问题示例

- 必须使用虚成员函数：
- `ppet->print();`

- 调用Dog类中的print成员函数
  - 因为它是虚函数

- C++在绑定调用前会先观察ppet指向何种对象

- 考虑:
  Pet vpet;
  Dog vdog;
  ...
  vdog = static_cast<Dog>(vpet); //ILLEGAL!
- 不能将Pet转型为Dog，但是:
  vpet = vdog; // Legal!
  vpet = static_cast<Pet>(vdog); //Also legal!
- 是可以的，因为向上转型是合法的
  - Upcast是指从子孙类型转型成祖先类型
