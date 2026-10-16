

## 匹配重载函数的顺序：

- （1）严格匹配
- （2）内部转换（相容类型匹配）
- （3）通过用户定义的转换寻找求一个匹配。

```cpp
void print(int);        void print(long);
void print(double);      void print(double);
void function()          void function()
{
    print(3);             int a;
    print(5.0);           print(a);//有二义性
    print('a');           }
    print(3.1415f);       print(long(a));
                          或者print(double(a));
```

## 重载的内部实现：

C++用名字粉碎（name mangling）（名字细分、名字压轧）的方法来改变变函数名。

用v,c,i,f,l,d,r 分别表示 void,char,int,float,long,double,longdouble.

```cpp
int f (char a);  // f_c
```

```cpp
int f (char a,int b,double c); //f_cid
```

## 返回值类型不能够作为重载依据（区分、细分重载）

```cpp
void func(int);
int func ( int);
fucn(10); //error
```

这样规定保证对重载的解析与环境无关

```cpp
float sqrt(float);
double sqrt(double);
void f(double da,float fla)
{
float fl=sqrt(da);  //调用sqrt(double)
double d=sqrt(da);  //调用sqrt(double)
fl=sqrt(fla);   //调用sqrt(float)
d=sqrt(fla);  //调用sqrt(float)
}
```

## 2-3 默认参数的函数

默认参数也称为缺省参量。

例： void delay(int loops);
    void delay(int loops)
{
    if (loops==0)
        return;
    for (int i=0;i<loops;i++);
}

将loops 定义成默认值为1000

```cpp
void delay(int =1000);
```

调用时： delay();
            delay(2000);

允许函数默认参数值，是为了让编程简单，让编译器做更多的检查错误工作。

## 默认参数函数的声明

当又有声明又有定义时，定义中不允许默认参数。

若只有定义，则默认参数才可出现在函数定义中

## 默认参数的顺序规定：

一个函数中可以有多个默认参数，默认参数应从右至左逐渐定义，当调用函数时，从左向右匹配参数。

例： void foo(int a, int b, bool c);

```cpp
void foo(int a, int b, bool c = false); //ok,c是最后一个参数
```

```cpp
void foo(int a, int b = 0, bool c);   //fail,b不是最后一参数
```

## 当调用有默认参数的函数时，从左向右匹配参数。

```cpp
#include <iostream>
using namespace std;
void fun(int a=1,int b=3,int c=5)
{
    cout<<"a="<<a<<", " <<"b="<<b<<", "
    <<"c="<<c<<","<<endl;
}
int main()
{
    fun();
    fun(7);
    fun(7,9);
    fun(7,9,11);
    cout<<"OK";
    return 0;
}
```

## 默认值的规定：

默认值可以是全局变量、全局常量、函数。不可以是局部变量。因为默认值是在编译时确定的，必须是静态确定的。

## 函数重载与函数默认参数：

(1)默认参数不能用于细分重载函数。

例1：

```cpp
void func(int,int);
void func(int=3,int=4);
func(22,32);
```

例2： void func(int);
void func(int,int);是重载函数
而void func(int);
void func(int,int=4);
在 func(3)调用时有二义性

## 应该避免重载过程中的涉及参数个数的默认设置

## （2）函数重载与函数默认参数：

默认函数可将一系列简单的重载函数合成一个。

```cpp
int month,int day,int year;
void Tdate()
{ month=4; day=15; year=1995;}
void Tdate(int m)
{ month=m; day=15; year=1995;}
void Tdate(int m,int d)
{ month=m; day=d; year=1995;}
void Tdate(int m,int d,int y)
{ month=m; day=d; year=y;}

void Tdate(int m=4,int d=15,int y=1995)
{
month=m; day=d; year=y;
}
```

```cpp
int main()
{
Tdate();
Tdate(1);
Tdate(1,2);
Tdate(1,2,3);
return 0;
}
```

如果参数值用来确定不同的操作，则用函数重载比较好

```cpp
#include <iostream>
using namespace std;
void print();
void print(int *);
int main()
{
    int arr[10];
    int sum=0;
    for (int i=0;i<10;i++){
        cin>>arr[i];
        sum=sum+arr[i];
    }
    if (sum>100)
        print(arr);
    else
        print();
    return 0;
}

void print(int * pa){
    cout<<"the array can be used"<<endl;
    for (int i=0;i<10;i++){
        cout<<pa[i]<<" ";
    }
    cout<<endl;
}

void print(){
    cout<<"the array can not be used<<endl";
}
```

## 无名参数

函数的定义和声明中，都可以省略形参名。

```cpp
void print (int ,int);
```

```cpp
void print(int a,int){
    cout<<a<<endl;
}
```

```cpp
void func(){
    print(1,2);
}
```

## 2-4： 程序运行时的内存布局

- (1) 代码区(code area)：存放程序的代码（各个函数的代码块）
- (2) 全局变量区(data area)：存放程序的全局数据和静态数据
- (3) 堆区(heap area)：存放程序的动态数据
  - 可以用malloc()与free()以及new和delete 来申请与释放堆内存，也称动态内存、动态数据区。
- (4) 栈区(stack area)：存放程序的局部数据（各个函数中的数据）

## 第三章： 指针和引用

### 3-1： 指针

#### 1. 指针变量的定义与赋值

指针是一种数据类型，用于存放内存单元的地址。

```cpp
int * ip;
```

定义同时赋值： int a; int *p=&a;

定义之后，单独使用赋值语句： int a,*p;

```cpp
p=&a;
```

int a[10],*p; p=a; p=&a[0];

## 3.与地址相关的运算 * 和 &

“ * ” 称为指针运算符（间接访问运算符），表示指针所指向的变量的值。一元运算符

```cpp
int a;    int *p=&a;  *p=5;
```

“ & ” 称为取地址运算符，用来得到一个对象的地址。一元运算符。

* 和 &是两个互逆的操作，当这两个操作符碰到一起时，其作用相互抵消，例如

```cpp
*&k=3    与
k=3
```

效果完全相同

## 4.用指针处理数组元素

例：

```cpp
int *p,i,a[6]={0,1,2,3,4,5};
p=a;
for(i=0;i<6;i++)
    printf("%d",_____);
```

a[i] *(a+i) p[i] *(p+i) *p++ *a++

考虑： []的作用 []和*的比较；越界访问 数组名和指针

- (1)数组名的内涵在于其指代实体是一种数据结构，这种数据结构就是数组；
- (2)数组名的外延在于其能够转换为指向其指代实体的指针，而且是个指针常量；
- (3)数组名作为函数形参时，在函数体内，其失去了本身的内涵，仅仅只是个指针；

```cpp
#include <iostream>
using namespace std;
void arrayTest(char str[])
//char *str, char str[10]
{cout << sizeof(str) << endl;
cout<<++str<<endl;
}
int main()
{
char str1[10] = "Y and me";
arrayTest(str1);
return 0;}
```

