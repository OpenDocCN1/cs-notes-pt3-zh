# 延迟求值(lazy evaluation)

+   - 若某个类中只有一部分内容改变时，将这些或声称为 mutable表示合适的。但是如果有批量或频繁修改，最好将该数据放入另外一个独立的对象里，并间接访问它

```
struct cache{
    bool valid;
    string rep;
}
class Date{
    cache* c;
    void cache_value() const;
public:
    string rep() const;
};
string Date::string_rep() const
{
    if(!c->valid){
        cache_value();
        c->valid = true;
    }
    return c->rep;
}
```

这种技术可以用于到类成员方式的延迟求值

# 10.2.8 结构体和类

+   - 按定义，'struct'类是与class一样，但是成员默认是公用的，也即：struct S{ ... }等价 class S { public: ... }的简写形式
+   - 一般情况下，struct被用来存放具有或几乎是公用的数据表
+   - 这种类是不完整的类，不足以构成数据表
+   - 结构中也可以有构造函数

```
class Date1 {
    int d, m, y;
public:
    int day() const;
    void add_year(int n);
};
class Date2{
    private:
    int d, m, y;
public:
    Date2(int dd, int mm, int yy);
    void add_year(int n);
};
```

上述两类声明了各自不同、完全备份

# 10.2.9 类内部定义的函数定义

+   - 如果一个函数是在类内定义的(不是简单的声明)，那么这个函数就被做为内联函数处理
+   - 也或者说，在类内部定义的函数应该很小，频繁使用的函数

```
class Date{
    int d, m, y;
public:
    int day() const
    { return d; }
}; // 声明和函数都在首部
class Date{
public:
    int day() const;
private:
    int d, m, y;
};
inline int Date::day() const
{ return d; }
```

# 10.3 高效的用户定义类型

前边所提及的是设计一个Date类的各种细节，本部分主要内容讨论设计一个简单而高效的Date类，并阐明语言的各种特性来如何支持这种设计

+   - 应用系统中会频繁的使用很多种抽象，例如：字符、整数、复数、向量、数组等，但C++直接支持其中一些最常见的抽象，但是，C++提供了使用用户定义类型的机制