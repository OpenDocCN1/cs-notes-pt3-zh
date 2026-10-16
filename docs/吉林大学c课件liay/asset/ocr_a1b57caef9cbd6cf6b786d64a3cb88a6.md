# 静态成员

```
class Student{
public:
    static int Get();
private:
    static int noOfStudents;
    int x;};
int Student::Get()
{return(noOfStudents);}
int Student::noOfStudents = 0;
void main()
{ cout<<Student::Get()<<endl;//正确
Student ss;
cout<<ss.Get()<<endl;}//不再需要
```

与静态数据成员一样，静态成员函数与类相关系，不与类的对象相关系，所以访问静态成员函数时，不需要对象。

静态成员函数的作用是为了处理静态数据成员