```
```cpp
class Complex
{
  double real,imag;
  public:
  Complex(){real=0;imag=0;}
  Complex(double r,double i){real=r;imag=i;}
  Complex operator + (const Complex &x) const
  {
    Complex temp;
    temp.real=real+x.real;
    temp.imag=imag+x.imag;
    return temp;
  };
};
```
```