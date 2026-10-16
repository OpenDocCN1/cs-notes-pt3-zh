```
常成员函数：
class R
{public :
R(int r1,int r2){R1=r1;R2=r2;}
add(){R2++;}
void print();
void print() const;//有效重载
void p() const;
private:
int R1,R2; };
void R::print()
{cout<<R1;p();//ok}
void R::print() const
{R1++; //error
add();//error
cout<<R1;p();//ok}
void p() const {cout<<R2<<endl;}
void main()
{
R a(5,4);
a.p();
a.print();//优先调用普通的成员函数
const R b(20,52);
b.print();
b.add();//error
b.p();
}
没有常构造函数和常析构函数，常对象和普通对象都调用同一构造函数和析构函数。
```