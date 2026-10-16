# 11.3.7 另一类成员函数

+   - 为了使得complex更好的工作，还可以定义复数相等函数，比如说：检查实部和虚部的值，然后利用这些函数进行各种有用的运算

```
class complex{
    double re, im;
public:
    double real() const { return re; }
    double imag() const { return im; }
};
inline bool operator==(complex a, complex b)
{
    return a.real()==b.real() && a.imag()==b.imag();
}
```

# 11.3.8 协助函数

+   - 将所有的东西集中到一起，complex就变成了

```
class complex
{
    double re, im;
public:
    complex(double r=0, double i=0) : re(r), im(i) {}
    double real() const { return re; }
    double imag() const { return im; }
    complex& operator+=(complex);
    complex& operator-=(double);
    // ==, !=, *, / == ...
};
```

# 协助函数

+   - 除此之外，还必须提供一批协助函数
+     - complex operator+(complex, complex);
+     - complex operator+(complex, double);
+     - complex operator+=(double, complex);
+     - // -, *, /, ...
+     - complex operator+(complex); // 一元正号
+     - complex operator-(complex); // 一元负号
+     - bool operator==(complex, complex);
+     - bool operator!=(complex, complex);
+     - ostream& operator<<(ostream&, complex&);
+     - ostream& operator>>(ostream&, complex&);

# 11.4 转换运算符

+   - 虽然通过构造函数来进行类型转换确实很方便，但是构造函数也无法达到
+     - 从用户类型到一个内部类型的转换（因为内部类型不是类）
+     - 从类类型到某个已有类型的转换（而不是修改那个已有类的声明）
+   - 这些问题可以通过为派生类定义转换运算符的方式解决
+   - 成员函数X::operator T()，其中T是一个类型名，定义了一个从X到T的转换