# # 第4章 运算符重载

# ## 何时用成员函数重载算符？

当一元运算符的操作数，或者二元运算符的左操作数是该类的一个对象时，重载运算符函数为成员函数

```
class Complex
{
    double dReal, dImag;
    public:
    Complex(double r, double i);
    Complex operator + (Complex &c2);
    Complex operator - ();
    Complex operator * (double d);
} ;
```