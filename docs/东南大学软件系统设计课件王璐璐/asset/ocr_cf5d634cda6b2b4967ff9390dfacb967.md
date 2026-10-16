# 构件重用…

a. 构造法：为了在子类中使用库中基类的属性和方法，可以考虑在子类中引进基类的对象作为子类的成员变量，然后在子类中通过成员变量重用基类的属性与方法。

b. 子类法：与构造法完全不同，子类法将子类直接说明为库中基类的子类，通过继承和修改基类的属性与行为完成新子类的定义。

```
```cpp
//下面采用构造法生成 Teacher 类
class Teacher{
public:
    Teacher(char *name, int age, char *teaching);
    ~Teacher();
protected:
    Person *Person;
    char *course;
};

//Teacher 类的实现
Teacher::Teacher(char *name, int age, char *teaching)
{
    //重用基类的方法 Person()
    Person=new Person(name, age);
    strcpy(course, teaching);
    return;
}
Teacher::~Teacher()
{
    delete Person;
}
```
```