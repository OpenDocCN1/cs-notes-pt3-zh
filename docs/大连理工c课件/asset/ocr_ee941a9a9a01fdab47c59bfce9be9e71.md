# # 第4章 运算符重载

```
class Complex
{
public:
    Complex(double r=0, double i=0){ dReal=r; dImag=i;}
    Complex complexAdd(Complex &c2) ;
private:
    double dReal, dImag;
};
Complex Complex :: complexAdd(Complex &c2)
{
    Complex c;
    c.dReal = dReal+c2.dReal;
    c.dImag = dImag+c2.dImag;
    return c;
}
c = c1. complexAdd( c2 );
```