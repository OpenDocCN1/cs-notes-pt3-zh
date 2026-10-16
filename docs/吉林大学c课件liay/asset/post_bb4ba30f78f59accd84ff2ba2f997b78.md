
## 8. 引用的使用—函数调用作为左值

```cpp
int a=0,b=0,c=0;
int & count(int k)
{
    if(k>60) return(a);
    if(k<=60&&k>30) return(b);
    if(k<=30) return(c);
}
int main()
{int i,j;
    for(i=0;i<15;i++)
    {
        cin>>j;
        count(j)++;
    }
    cout<<a<<b<<c;
    return 0;
}
```

## 分析程序，写出结果：

```cpp
#include <iostream.h>

void main()
{
    int* p;       int*& rp=p;
    int x=100;    int &rx=x;
    p=&x;
    cout<<"*p="<<*p<<endl;
    cout<<"x="<<x<<endl;
    cout<<"rx="<<rx<<endl;
    cout<<"*rp="<<*rp<<endl;
    x++;    (*p)++;
    rx++;   (*rp)++;
    cout<<"*p="<<*p<<endl;
    cout<<"x="<<x<<endl;
    cout<<"rx="<<rx<<endl;
    cout<<"*rp="<<*rp<<endl;
}
```

## 第四章： 类

### 1.从结构到类

结构：相关联的数据元素组成一个单独的统一体

```cpp
struct Savings
{
    unsigned accountnumber; //账号
    float balance;//结算额
};
```

‘；’是必需的

struct Savings a,b;
或者 Savings a,b; 常用形式

结构分量称为成员，使用“.”操作符访问成员

```cpp
void fn()
{
Savings a;
Savings b;
a.accountnumber=1;
b.accountnumber=2;
}
```

粗糙的数据类型，没有涉及复合数据的操作。C的结构中不含有成员函数。

C++的类中既能包含数据成员，又包含函数成员或称成员函数。

```cpp
class Savings
{
    public:
        float deposit(float amount) //成员函数
        {
            balance+=amount;
            return balance;
        }
        unsigned accountnumber; //数据成员
        float balance;//结算额
};  //类的声明时不分配内存空间
```

```cpp
void fn()
{Savings a,b;    //对象                (对象和变量)
    Savings *pa=&a,*pb=&b;  //对象指针
    a.accountnumber=123;   pb->accountnumber=456;
    pa->balance=1000;      b.balance=2000;
    a.deposit(100);        pa->deposit(200);
    (*pb).deposit(100);    (&b)->deposit(200);
}
```

注意：'.'的前面是对象，'->'的前面是地址，成员函数的调用一定是和某个对象捆绑在一起。

## C++中类与结构的区别

```cpp
struct Savings
{
public :    //可省略
    float deposit(float amount)
    {
        balance+=amount;
        return balance;
    }

private:
    int accountnumber;
    float balance;
};
```

```cpp
class Savings
{
private: //可省略
    int accountnumber;
    float balance;

public:
    float deposit(float amount)
    {
        balance+=amount;
        return balance;
    }
};
```

## C++中类与结构的区别：

默认情况下，class定义的成员是private的，而struct定义的成员是public的。

### 2.对象的引用以及返回对象的函数

```cpp
class Student
{
public:
    int age;
    char name[9];
    float score;
};
```

```cpp
int main()
{
    void add(Student&);
    Student get();
    Student a[30];
    for(i=0;i<30;i++)
        add(a[i]=get());
    return 0;
}
```

```cpp
void add (Student &b)
{
    if(b.age<20)
        b.age++;
}
```

```cpp
Student get()
{ Student temp;
    cin>>temp.age;
    cin>>temp.name;
    cin>>temp.score;
    return(temp);
}
```

### 3. 公有&保护&私有成员

```cpp
class Student{
    public:
        float score;
        void p(){ age=20;}
        void q() {add();}
        void r(int a){cout<<a;}
    private: //和protected只有继承区别
        int age;
        void add(){score=0;p();age++;}
};
```

```cpp
int main()
{Student a;
a.p();
a.q();
a.score=80;
a.age=20;    //错误
a.add();     //错误
a.r(5);
a.r((int)(a.score));
a.r(a.age);  //错误
return 0;
}
```

### 4.成员函数&非成员函数

```cpp
class Student{
    public:
        void p(){
            age=20;
            cout<<age;
        }
        int q(){return(age);}
        float score;
    private:
        char name[9];
        int age;
};
```

```cpp
void p(int a)
{
    cout<<a;
}
int main()
{Student a;
    a.p();
    p(a.q());
    return 0;
}
```

## 成员函数与普通函数的区别：

- 成员函数属于类，成员函数定义是类设计的一部分，其作用域是类作用域。而普通函数一般为全局函数
- 成员函数的操作主体是对象，使用时通过捆绑对象来行使其职责，而普通函数被调用时没有操作主体

### 5. 重载成员函数

```cpp
class Student
{
public:
float grade(){//...}
float grade(float newgpa){//...}
protected:
//....
};
class Slope{
public:
float grade(){//...}
protected:
//....
};
char grade(float value){//...}

void main()
{
Student s;
Slope t;
s.grade(3.2);
float v=s.grade();
char c=grade(v);
float m=t.grade();
}
```

### 6.定义成员函数

（1）在类的内部定义成员函数

```cpp
#include <iostream>
using namespace std;
class Tdate{
public:
void set (int m,int d,int y)
{month=m;day=d;year=y;}
int isleapyear()
{return (year%4==0&&year%100!=0)||(year%400==0);}
void print()
{cout <<month<<"/"<<day<<"/"<<year<<endl;}
private:
int month;
int day;
int year;
};

int main(){
Tdate a;
a.set(2,4,1998);
a.print();
if (a.isleapyear())
cout<<"is leapyear!";
else
cout<<"is not leapyear!";
return 0;}
```

set 与 month 全名

::作用域区分符、作用域运算符、名字空间引导符
