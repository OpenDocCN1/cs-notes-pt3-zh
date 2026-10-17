# # 公有继承的测试

```
class B : public A
{
public :
    int get_S() { return s ;};
    void make_S() { s = x * y ; }; // 使用基类数据成员x, y
protected:
    int s;
};
class C : public B
{
public :
    void get_H() { cout << "Enter h : " ; cin >> h ; }
    int get_V() { return v ; }
    void make_V()
    { make_S(); v = get_S() * h ; } // 使用基类成员函数
protected:
    int h, v;
};
```

```
1. A类的x、y换为private如何？
2. class B : private A
3. void make_V()
{ make_S(); v = x*y*h ; }
```