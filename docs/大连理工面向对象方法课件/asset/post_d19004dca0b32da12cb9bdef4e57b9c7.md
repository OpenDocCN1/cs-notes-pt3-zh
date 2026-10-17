
```text
Military time after set Time is 13:27:06
Standard time after set Time is 1:27:06PM

After attempting invalid settings:
Military time: 00: 00: 00
Standard time: 12: 00: 00AM
```

## 小结：

- 1. 若在main 中写成：t.hour（t.second, t.minute）错误？
   不能访问类的私有成员。只能通过类的成员函数访问。
- 2. 提倡编写与实现无关的程序，如果与实现无关的代码所用到的类的实现发生了改变，那么使用它的代码无需改动（但需要重新编译）。
- 3. 要保持类的所有数据成员都是私有的，然后给客户提供设置或者获取私有数据成员值的公有成员函数，这样有利于对客户隐藏类的实现。减少了意外的错误和提高了程序的可修改性。（类的客户可能是另一个类的成员函数或一个全局函数），类的客户不关心类的内部是怎样实现其功能的，他不能访问类的私有成员。

## 三、成员函数和this指针

类的成员函数可以是：

（1）非静态的　　（2）静态的

### （1）先介绍非静态成员

对于非静态成员函数，类的成员函数是如何区分不同对象的数据成员的呢？

- 事实上，对于每一个类的非静态成员函数，都有一个隐含的this指针，该指针指向调用该成员函数的对象。
- 当成员函数使用对象中的非静态成员（无论是成员变量还是成员函数），它事实上是通过this指针来调用该成员的。

例如：

```cpp
class MyClass
{
private:
    int i;
public:
    void seti(int newi)
    {
        i=newi; // i 成员变量
    }
};
```

对编译器而言，成员函数seti的定义事实上如下面的代码所示：

```cpp
void seti(int newi)
{
    this->i=newi;
}
```

对于以不同方式定义的成员函数，this指针具有不同的类型。在上面的seti函数中，this指针的类型为MyClass* const，这表明，this指针是一个常指针，即：程序中可能通过this指针来修改类中的成员的值，但不可以修改this指针本身的值。也就是说，不可以对this指针重新赋值，以使它指向另一个对象。

现在假设我们在类MyClass中定义了另一个成员函数geti，如下面的代码所示：

```cpp
int geti() const
{
    return i;
}
```

在上面的代码中，const关键字表明函数geti不会修改调用该成员函数的对象中的成员的值。对于编译器而言，上面的成员函数geti是这样的：

```cpp
int geti() const
{
    return this->i;
}
```

由于使用了const关键字，则this指针的类型为const MyClass* const，这表明不但不能修改this指针本身，也不能通过this指针修改对象中的成员。例如，如果我们按如下方式定义seti函数：

```cpp
void seti(int newi) const
{
    i=newi;
}
```

结果怎么样？上面的代码将会导致编译错误。

● 注意：一般情况下我们不需要显式地使用this指针。下面的代码代表了this指针的一个典型应用：

请看实例：`\\c第三讲\Example\显式this指针使用\this.cpp`

`\\c第三讲\Example\隐式this指针使用\pthis.cpp`（略讲）

### （2）静态成员

前面说过，无论是类中的成员变量还是成员函数，都可以声明为静态的。类的静态成员在工作方式上和非静态成员有很大的差别。所以单独讲述。

### 1. 静态成员变量

先看一个静态数据成员的例子。

```cpp
#include <iostream.h>
class MyClass
{
    public:
        static int i;   //静态成员变量 i
};

int MyClass::i;
void main()
{
        MyClass cls1;
        MyClass cls2;
        cls1.i=1;
        cout<<"cls1.i="<<cls1.i<<" cls2.i="<<cls2.i<<endl;
        cls2.i=2;
        cout<<"cls1.i="<<cls1.i<<" cls2.i="<<cls2.i<<endl;
}
```

上面的示例程序的运行结果如下：

```text
cls1.i=1 cls2.i=1
cls1.i=2 cls2.i=2
```

出现这样结果的原因：是静态数据成员和非静态数据成员的一个极大的不同之处。对于同一个类的所有对象，C++只为它们维护了一份静态变量的拷贝，通过每一个对象对这些静态变量进行操作，事实上都是对同一个数据区域进行操作。这就可以解释上面的运行结果了，无论我们使用表达式`cls1.i`还是表达式`cls2.i`，它们都是对同一个`i`进行操作，很自然，使用表达式`cls1.i`修改了静态成员`i`的值，表达式`cls2.i`的值会立即反映所作的修改。

### 2. 静态成员函数

前面已经讲过，不像非静态成员函数那样，静态成员函数没有隐含的this指针，因此，它们只能访问类中的静态数据成员等（另外还有只能访问类中的枚举和嵌套类型）。而且，同静态数据成员一样，调用静态成员函数不需要有类的实例对象。看下面的例子：

例如：请看实例：`\c\第三讲\Example\example_4\example_4.cpp`

```cpp
#include <iostream.h>
class MyClass
{
public:
	static int Count()
	{
		return nCount;
	}
	static void Add(int NewElement) // 函数 Add(int NewElement)
	{
		nCount++;
	}
private:
	static int nCount;
};
int MyClass::nCount=0;
void main()
{
	cout<<"Count="<<MyClass::Count()<<endl;
	for (int i=1; i<=5; i++)
	{
		MyClass::Add(i);
	}
	cout<<"Count="<<MyClass::Count()<<endl;
}
```

- 我们没有定义一个类MyClass的对象，但仍可以使用其中的所有公有的静态数据成员和静态成员函数。上面的示例程序的运行结果如下：

```text
Count=0
Count=5
```

同非静态成员函数相比，静态成员函数的使用受到如下的限制：

- 1. 不能在静态成员函数中直接访问类中的非静态成员；
- 2. 不能将静态成员函数定义为虚函数。

注意：

- 可以仅在类中声明其静态成员函数，然后在类的外部添加其定义，但这并不是必须的。可以在类中声明静态成员函数的同时定义它们。
- 同静态数据成员一样，如果使用成员选择运算符“.”和“->”来调用类的静态成员函数，表达式中运算符“.”和“->”前面的表达式不会被求值，如果在这一部分进行了函数调用，则这些函数永远也不会真正的被调用。

再看一个例子

### 例子：静态数据成员与非静态数据成员的区别

`\第三讲\Example\example_5\example_5.cpp`

```cpp
#include <iostream.h>
#include <stdlib.h>
class counter
{
        static int count;  //静态成员
                int objnumber;//非静态成员
public:

        counter(){
                count++;
                objnumber=count;
        }

        void show(){
                cout<<"obj"<<objnumber<<"\n";
                cout<<"count="<<count<<"\n";
        }
};
int counter::count=0;//初始化（out of the class）
main()
{

        counter obj1;
        obj1.show();
        cout<<"---------------\n";
        counter obj2;//需要仔细看、分析
        obj1.show();
        obj2.show();
        cout<<"------------\n";
        counter obj3;
        obj1.show();
        obj2.show();
        obj3.show();
        cout<<"------------\n";
        return 0;
}
```

（the result is:）

```text
obj1 count=1
obj1 count=2
obj2 count=2
obj1 count=3
obj2 count=3
obj3 count=3
```
