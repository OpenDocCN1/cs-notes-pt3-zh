# II组合类的构造函数如何工作

```
class StudentID{
public:
    StudentID(int id=0)
    { value=id;}
    ~StudentID() {}
protected:
    int value;
};
```

```
int main()
{
    Student s("Randy",9818);
    return 0;}
```

```
class Student{
string name;
StudentID id;
public:
    Student(string pName= "noName" ,int ssID=0):id(ssID)
    {
        name = pName;
    }
};
```

冒号语法
用冒号引出构造函数的调用表（初始化列表）
用构造参数列表中说明的参数去调用构造函数