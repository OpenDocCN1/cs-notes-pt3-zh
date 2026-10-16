# //带参数的构造函数

```
#include <iostream>
#include<string>
using namespace std;
class Student{
    public:
    Student(string pName, int i,float j)
    { cout <<"构造学生" <<pName <<endl;
    name = pName;
    semesHours=i;
    gpa=j;
    }
    ~Student()
    {  cout <<"析构 " <<name <<endl; }
    //其它公共成员
    private:
    string name;  int semesHours;  float gpa;
};

void f()
{Student t("Tom", 17, 90);}
int main()
{ Student ss("Jenny", 20, 80.5);
 f();
 return 0; }
```