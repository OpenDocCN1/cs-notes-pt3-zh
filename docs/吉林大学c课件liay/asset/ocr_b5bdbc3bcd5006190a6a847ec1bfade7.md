```
//多级派生
class Student{
public:
    int m1;
protected:
    int m2;
private:
    int m3;
};
class Master :public Student
{
public:
    int n1;
protected:
    int n2;
private:
    int n3;
};
```

```
class MasterEnginee :public Master{
public:
    int p1;
protected:
    int p2;
private:
    int p3;
};
```

```
void main()
{ MasterEnginee a;
}
```

直接基类：直接参与派生出某类的基类。
间接基类：基类的基类，甚至更高层的基类。
直接派生类
间接派生类