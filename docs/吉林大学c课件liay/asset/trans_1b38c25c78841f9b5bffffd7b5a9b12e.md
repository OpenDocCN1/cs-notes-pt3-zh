

# 构造
析构函数

```
class aa {
public:
    aa(int a=1){id=a;cout<< "构造" <<endl;}
    aa (aa & s){id = s.id;cout<< "拷贝" ;}
    int & Getid(){return(id);}
private:
    int id;
};
int main()
{ aa m;      // "构造"
    aa n(m);  // "拷贝"
    aa o = m; // "拷贝"  和aa o(m)等价
    aa s = 9; // "构造"  和aa s(9)等价
    aa t;     // "构造"
    t = 9;    // "构造"、 赋值运算
    return 0; }
```

# 类型转换

# 构造
析构函数

```
class aa {
    public:
        aa(int a=1){id=a;}
        char * p;
        int id;
};

void m(aa a)
{cout<<a.id<<endl;}

int main()
{
    m(9); //相当于m(aa(9));
    return 0;
}//如果存在m(int)的函数则优先匹配
```

# 类型转换

# 构造
析构函数

```
class aa {
    public:
        aa(int a=1){id=a;}
        int id;
};
class bb {
    public:
        bb(int a=2){id=a;}
        int id;
};
void m(aa a)
{cout<<a.id<<endl;}
void m(bb a)
{cout<<a.id<<endl;}
int main()
{  m(9); //存在二义性;
    return 0;
}//转换不能太复杂，不允许多参数，不允许间接转换
```

# 构造

# 析构函数

```
class HighWorker {
  float income;
  public:
    HighWorker(float a = 2000.0){income = a;}
    float Getincome(){return(income);}
};
class Worker {
  float income;
  public:
    Worker(float a = 1200.0){income = a;}
    Worker(HighWorker b){income = 0.75*b.Getincome();}
    float Getincome(){return(income);}
};
void m(Worker a){cout<<a.Getincome()<<endl;}
int main(){ Worker a; m(a);
    HighWorker b; m(b);
    return 0;}
```

常对象：数据成员值在对象的整个生存期内不能被改变。

即常对象定义是必须进行初始化，而且不能被更改。

声明的语法形式：

const 类名 对象名 或者 类名 const 对象名

```
Class A
{public:
A(int i, int j) {x=i;y=j;}
reset(){x++;y++;}
private:
int x,y;
};
A const a(3,4);
a.reset();//error
```

```
常成员函数：
class R
{public :
R(int r1,int r2){R1=r1;R2=r2;}
add(){R2++;}
void print();
void print() const;//有效重载
void p() const;
private:
int R1,R2; };
void R::print()
{cout<<R1;p();//ok}
void R::print() const
{R1++; //error
add();//error
cout<<R1;p();//ok}
void p() const {cout<<R2<<endl;}
void main()
{
R a(5,4);
a.p();
a.print();//优先调用普通的成员函数
const R b(20,52);
b.print();
b.add();//error
b.p();
}
没有常构造函数和常析构函数，常对象和普通对象都调用同一构造函数和析构函数。
```

友元

引入

```
class aa{
    float a;  float b;
public:
    float &aaa(){return(a);}
    float &bbb(){return(b);}
};
aa sum(aa a,aa b)
{ aa c;
 c.aaa()=a.aaa()+b.aaa(); c.bbb()=a.bbb()+b.bbb();
    return(c);
}
void main()
{ aa a,b;
    a.aaa()=1; a.bbb()=2;  b.aaa()=3; b.bbb()=4;
    aa c=sum(a,b);
    cout<<c.aaa()<<endl<<c.bbb();
    for(long i=0;i<100000;i++) cout<<a.aaa()<<endl;
```

# 友元
希望

```
class aa{
    float a;  float b;
public:
    float &aaa(){return(a);}
    float &bbb(){return(b);}
};
aa sum(aa s,aa t)
{ aa c; c.a=s.a+t.a; c.b=s.b+t.b;
    return(c);
}
void main()
{ aa a,b;
    a.a=1; a.b=2;
    b.a=3; b.b=4;
    aa c=sum(a,b);
    cout<<c.a<<endl<<c.b;
    for(long i=0;i<100000;i++) cout<<a.a<<endl;
}
```

# 友元

# 实现

```
class aa{
    float a;  float b;
    public:
        friend aa sum(aa,aa);
        friend void main();//友元函数，具有类的成员函数的访问权限
        float &aaa(){return(a);}
        float &bbb(){return(b);}
};
aa sum(aa s,aa t)
{  aa c; c.a=s.a+t.a; c.b=s.b+t.b;
    return(c); }
void main()
{ aa a,b;
    a.a=1; a.b=2;
    b.a=3; b.b=4;
    aa c=sum(a,b);
    cout<<c.a<<endl<<c.b;
    for(long i=0;i<100000;i++) cout<<a.a<<endl; }
```

# //友元类

```
class Teacher; //前置说明——类名说明，解决交叉声明的方法
class Student{
    friend void Teacher::p(int);
    friend void Teacher::q(float);
    friend class Teacher;
    int age; float score;
};
class Teacher{
public:
    void p(int a){Sooc.age = a;}
    void q(float a){Sooc.score = a;}
    Student Sooc;
private:
    char name[9];
};
void main()
{ Teacher a; a.p(20); a.q(80.9);}
```

友元类的所有成员函数都可视为该类的友元函数，能存取该类的私有成员和保护成员。

注意：
友元关系不具有对称性。
友元关系不具有传递性.如果类B是类A的友元类，类C是类B的友元类，这并不隐含类C是类A的友元类。

# 对手使用友元：

- 1. 说明的位置既可在public区，也可在protected区。友元函数虽然是在类内进行声明，但它不是该类的成员函数，不属于任何类。
- 2. 在类外定义友元函数，与普通函数的定义一样，一般与类的成员函数放在一起，以便类重用时，一起提供其友元函数。
- 3. 友元函数是能访问类的所有成员的普通函数，一个函数可以是多个类的友元函数，只需在各个类中分别声明。
- 4. 友元能使程序精炼，提高程序的效率。
- 5. 友元破坏了类的封装，使用时，要权衡利弊，在数据共享与信息隐藏之间选择一个平衡点。

