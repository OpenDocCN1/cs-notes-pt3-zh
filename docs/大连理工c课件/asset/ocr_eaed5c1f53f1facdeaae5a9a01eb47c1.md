# # 第4章 运算符重载

class Complex
{ public:
Complex(double r, double i){ dReal=r; dImag=i;}
Complex operator + (Complex &c2);
private:
double dReal, dImag;
};

c = c1 + c2; // c1.operator+(c2)

Complex Complex::operator + (Complex &c2)
{ Complex c;
c.dReal = dReal+c2.dReal;
c.dImag = dImag+c2.dImag;
return c;
// return Complex( dReal+c2.dReal, dImag+c2.dImag);
}