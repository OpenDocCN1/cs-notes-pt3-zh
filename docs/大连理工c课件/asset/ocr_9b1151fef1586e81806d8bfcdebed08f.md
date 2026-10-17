# # 第4章 运算符重载

# ## 成员函数重载算符

```
class Complex
{
    double dReal, dImag;
    public:
    Complex(double r=0, double i=0);
    Complex operator + (Complex &c2);
    Complex operator + (double d);
};
```

```
Complex z ( 2.0 , 3 ) , k ( 3 , 4.5 ) ;
z = z + k;
k = z + 27 ;
k = 27 + z ;
```

![](bbox=[0.458, 0.741, 0.788, 0.825])

![](bbox=[0.505, 0.821, 0.839, 0.904])

![](bbox=[0.549, 0.902, 0.671, 0.986])