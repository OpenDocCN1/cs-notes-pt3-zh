

```
class Student{
public:
    Student();  // 构造函数的声明
    ~Student(); // 析构函数的声明；没有参数；不可以重载
protected:
    char *name;
    int age;
};
Student::Student()
{ age=5; }
Student::~Student()
{ cout<< "对象结束了"; }
int main(){
    Student a;
    Student b;
    return 0;
}//析构函数的调用顺序和对象构造的顺序相反
```

//对象生命周期结束时由系统自动调用

析构函数不是删除对象，而是在撤销对象占用的内存之前完成一些清理工作。还可以用来执行用户希望在对象生命周期结束时所执行的任何操作。

## 构造、析构函数

```
class Student{
public:
    void Student(); //错误
    void ~Student();//错误
protected:
    char *name;
    int age;
};
void Student::Student()//错误
{ age=5;
}
void Student::~Student()//错误
{ cout<< "对象结束了" ;
}
Student a;
```

```
class Student{
public:
    Student();
    ~Student();
protected:
    char *name;
    int age;
};
Student::Student(){ age=5;}
Student::~Student()
{ cout<<"对象结束了";}

Student a;
a.Student(); //错误
a.~Student(); //不提倡
```

## C++标准程序库中的string类

string name;

自动处理空间的占用问题。C++字符串并不以’ \0’ 结尾。

可以用 = 进行赋值操作， == 进行比较， + 做串联。

使用时#include <string> //注意这里不是string.h

```
string str1,str2= “abcd” ;
```

```
str1=str2;
```

```
str2=str1+” 123” ;
```

```
cout<<str2<<" "<<str2.length()<<" "<<str2.insert(0,"8");
```

由C++字符串得到对应的C_string的方法是使用data()、c_str()

data()以字符数组的形式返回字符串内容，但并不添加’ \0’ 。

```
char s[20];strcpy(s,str1.data());
```

c_str()返回一个以 ‘\0’ 结尾的字符数组， strcpy(s,str2.c_str())

## //带参数的构造函数

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

## 构造、析构函数

```
class A {
public:
    int s;
};
A a1;
```

对于没有显性构造函数的类系统都自动提供一个默认构造函数

```
A() { }
```

用户没有定义析构函数，编译器自动生成一个析构函数。

```
~A() { }
```

## //构造函数重载

```
class Student{
public:
    Student(string pName)
    { cout <<"姓名" <<pName <<endl;
        name = pName;
    }
    Student(string pName,int i)
    { cout<< "姓名学时"<<endl;
        name = pName;
        semesHours=i;
    }
private:
    string name; int semesHours;
};
int main()
{ Student tt("Tom",60); Student ss("Jenny");
    Student f;    //错误  ?
    return 0;
}
```

如果手工定义了任何的构造函数，系统不再提供默认的无参构造函数。

## 构造、析构函数

```
//构造函数重载
class Student{
public:
Student(string pName) {
    cout <<"姓名" <<pName <<endl;
    name = pName; }
Student(string pName,int i) {
    cout<<"姓名学时"<<endl;
    name = pName;   semesHours=i; }
Student(){}
protected:
string name; int semesHours;
};
void main(){
Student tt("Tom",60); Student ss("Jenny");
Student f;   } //不错
```

自定义无参构造函数将替代缺省构造函数的存在

## 构造、析构函数

//默认值构造函数 改写重载构造函数

```
class Student{
public:
Student(string pName="",int i=0)
{ cout<<"姓名学时"<<endl;
name = pName;
semesHours=i;
}
protected:
string name; int semesHours;
};
int main()
{ Student tt("Tom",60); Student ss("Jenny");
Student f; //不错
return 0; }
```

Student f();
Student g(int);声明函数

无名对象（一次性对象）：Student("Jane");
一般作为实参，用在创建后不需要反复使用的场合。

- 构造函数是特殊的类成员函数。
- C++规定与类同名的成员函数是构造函数，在该类的对象创建时，自动被调用。
- 构造函数负责对象的初始化
- 可拥有多个参数。可以重载。
- 构造函数不返回具体的值，不指定函数的返回类型。
- 可内置定义，也可以在类外定义。
- 通常是Public的

- 析构函数也是一个特殊的成员函数；
- 作用与构造函数相反；在对象的生命周期结束时自动被调用。
- 名字是类名前加一个~；
- 不返回任何值；没有函数类型，没有函数参数，因此不能被重载。
- 一个类可以由多个构造函数，只能有一个析构函数。
- 可内置定义，也可以在类外定义。
- 用于清理和释放资源的工作。
- 通常是Public的

## 构造、析构函数

```
class A{
public:
    int s;
private:
    A(){cout<<"A is constructing\n";};
    ~A(){cout<<"~A\n";}
};
int main(){
    A s;  //出错
    return 0;}
//构造函数&析构函数的属性影响
```

## 判断对错，错误写出原因：

- 1、 使用 **struct** 定义的类中默认的访问权限是 **private** 的
- 2、 **this** 不能被非成员函数访问
- 3、 任何情况下 **private** 权限的内容不能被类外访问
- 4、 引用破坏了函数的封装性
- 5、 内联函数的作用是提高系统的效率
- 6、 不同类的成员函数也可以重载
- 7、 参数类型、函数返回类型可以作为函数重载的依据

组合：是指结构和类的声明嵌入结构变量和对象作为其成员的现象。
嵌入的对象成员称为成员对象(类成员)。
包容这个成员对象的类称为组合类或包容类。

