```
class Student{
int move_tel;
public:
    int id;
};
class Master :public Student
{ string topic;
public: //方法略
};
class Phd:public Student{
string professor;
public: //方法略
};
class DoubleMaster
:public Student{
string SecondMajor;
public://方法略
};
class Member{
    Student * m[128];
public:
    Student * &f(int k)
    {return(m[k]);}
};
void main()
{Member s;
    s.f(0)=new Student;
    s.f(1)=new Master;
    s.f(2)=new Phd;
    s.f(3)=new DoubleMaster;
    s.f(4)=new Phd;
    //。。。 。。
}
//希望定义一个t，并完全拷贝s内容
```