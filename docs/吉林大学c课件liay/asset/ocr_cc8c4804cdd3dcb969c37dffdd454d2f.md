# 静态成员

```
//静态成员的需要性
StudentID.h
class StudentID{
    int value;
public:
    StudentID();
    ~StudentID();
};
```

```
StudentID.cpp
int ID=0;
StudentID::StudentID()
{   value=++ID;}
StudentID::~StudentID()
{   --ID;}
```

```
aa.Cpp
#include "StudentID.h"
extern int ID;
void main()
{ void xx();
    StudentID s,t;
    cout<<ID;
    xx();
    cout<<ID;
}
```

```
bb.Cpp
#include "StudentID.h"
extern int ID;
void xx()
{ ID++;}
```