# 多重继承

```
class Student {public: int id;};
class Master :public Student{
public:
Master(string p){practice = p;}  string practice;
};
class Phd:public Student{
public:
Phd(string p){paper = p;}   string paper;
};
class M_p:public Master,public Phd {
public :
M_p(string p,string q):Master(p),Phd(q){}
float avg;
};
void main()
{M_p a("c++","KDD");  a.avg=85.9;
cout<<a.practice<<a.paper;  a.id=1;  a.PhD::id=1;
Student * p=&a;   a.Student::id=1;}
```