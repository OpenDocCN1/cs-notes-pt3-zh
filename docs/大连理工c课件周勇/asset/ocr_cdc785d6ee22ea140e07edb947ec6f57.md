# # 设计有理数类/分数类

```
class Rational{
public:
    Rational(int nn=1,int mm=1); //构造函数
    void print() ;    // 输出化简的 分子/分母
    void simple();    // 约分
    double getValue();    // 返回分数值
    Rational add(Rational & A);    // r = r1.add(r2);
    void sub(Rational & A , Rational &B); // r.sub(r1,r2);
    Rational mul(Rational & A);
    void _div(Rational & A, Rational &B);
private:
    int m; // 分母
    int n; // 分子
};
```