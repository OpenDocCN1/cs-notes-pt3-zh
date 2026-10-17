# ## 5.8 继承中的同名成员访问

```
class Student
{
protected:
    int id;
};
```

```
class Teacher
{
protected :
    int id;
};
```

```
class Assistant: public Student, public Teacher
{
    public:
    void print(){
    cout<<id<<endl; //error!访问是二义的
    cout<<Student::id<<endl; //访问Student的id
    cout<<Teacher::id<<endl; //访问Teacher的id
    }
};
```