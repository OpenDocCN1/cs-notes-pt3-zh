# 第3章 类与对象

3.10 友元函数和类

# 例3.14 成员函数作类的友元函数

```
class Line
{
private:
    double a, b, c;        //直线为ax+by+c=0的系数
public:
    Line(double a=0.0, double b=0.0, double c=0.0);
    void disp();
    friend double Point::distance(Line l); //声明为Line的友元
};
Line::Line(double a, double b, double c){
    this->a = a; this->b = b; this->c = c;   }
void Line::disp() {
    cout<<"线 ("<<a<<"x+"<<b<<"y+"<<c<<"=0 )";}
```