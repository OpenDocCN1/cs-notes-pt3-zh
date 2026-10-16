# 构造、析构函数

```
#include <iostream>
using namespace std;
class Student{
public:
    Student(int i)
    { value=i; cout<<"Student"<<value<<endl; }
    ~Student(){cout<<"~Student"<<value<<endl;}
protected:
    int value;
};
int main()
{
    Student(9);// 无名对象，正确
    Student *p=&Student(8);//错误
    Student &q=Student(7);//正确，无名对象将在它的引用离开作用域时销毁
    Student i(6);
    i = Student(5);//正确
    return 0;
}
```

+   Student9
+   ~Student9
+   Student8
+   ~Student8
+   Student7
+   Student6
+   Student5
+   ~Student5
+   ~Student5
+   ~Student7