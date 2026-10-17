
![](img/3b4669cf00b2833fe526284506f3f342_174_0.png)

对 instrument 的引用产生如下结果：编译器从这个 instrument 指针开始，这个指针指向这个对象的起始地址。所有的 instrument 对象或由 instrument 派生的对象都有它们的 VPTR，它在对象的相同的位置（常常在对象的开头），所以编译器能够取出这个对象的 VPTR。

VPTR 指向 VTABLE 的开始地址。所有的 VTABLE 有相同的顺序，不管何种类型的对象。play() 是第一个，what() 是第二个，adjust() 是第三个。所以编译器知道 adjust() 函数必在 VPTR+2 处。这样，不是“以 instrument::adjust 地址调用这个函数”（这是早捆绑，是错误的行为），而是产生代码，“在 VPTR+2 处调用这个函数”。因为 VPTR 的效果和实际函数地址的确定发生在运行时，所以这样就得到了所希望的晚捆绑。向这个对象发送消息，这个对象能够决定它应当做什么。

![](img/3b4669cf00b2833fe526284506f3f342_174_1.png)

### (3) 揭开谜底

如果能看到由虚函数调用而产生的汇编语言代码将非常有帮助，这样可以看到晚捆绑实际上是如何发生的。

下面是在函数 f(instrument & i) 中调用：

i.adjust(1);

结果是这个对象将产生的输出。

```
push 1 //1入栈

push si//this指针（指向brass object）入栈

mov bx,word ptr [si] //this所指内容（即vptr）进入bx

call word ptr [bx+4]//调用具体函数

add sp,4//恢复堆栈
```

C++ 函数调用的参数与 C 函数调用一样，是从右向左进栈的。（这个顺序是为了支持 C 的变量参数表），所以参数 1 首先压栈。在这个函数的这个地方，寄存器 si 存放 i 的首地址。因为它是被传递对象的首地址，它也被压进栈。请大家记住：这个首地址对应于 this 的值。正因为调用每个成员函数时 this 都必须作为参数压进栈，所以成员函数知道它工作在哪个特殊对象上。这样，我们总能看到，在成员函数调用之前压栈的次数等于参数个数加一（除了 static 成员函数，它没有 this）。

如何实现实际的虚函数调用？首先，必须产生 VPTR，使得能找到 VTABLE。由于 VPTR 在对象的开头，所以 this 的内容对应于 VPTR。所以 mov bx, word ptr [si] 取出 si（即 this）所指的字，它就是 VPTR。将这个 VPTR 放入寄存器 bx 中。放在 bx 中的这个 VPTR 指向这个 VTABLE 的首地址，但被调用的函数在 VTABLE 中不是第 0 个位置，而是第 2 个位置（因为它是这个表中的第三个函数）。对于这种内存模式，设每个函数指针是两个字节长，所以编译器对 VPTR 加 4，计算相应的函数地址所存在的地方，注意，这是编译时建立的常值。所以我们只要保证在第二个位置上的指针恰好指向 adjust()。幸好编译器仔细处理，并保证在 VTABLE 中的所有函数指针都以相同的次序出现。

一旦在 VTABLE 中相应函数指针的地址被计算出来，就调用这个函数。所以取出这个地址并马上在这个句子中调用：

call word ptr [bx+4]

最后，栈指针移回去，以清除在调用之前压入栈的参数。在 C++ 的汇编代码中，我们将常常看到调用者清除这些参数。但这依处理器和编译器的实现而有所变化。

（续）public、private 和 protected，它们的作用我们将在下面作说明，**base-class** 是基类的类名。

与指定类中的成员的访问权限相仿，我们可以使用访问限定关键字指定派生类对基类成员的访问权限。

**注意：对于使用不同继承方式（public、private 和 protected）派生的类，对于基类中以不同方式（public、private 和 protected）定义的成员的访问限制是不同的。**有关内容见表所示。

表 不同派生方式得到的派生类对基类成员的访问权限

| 基类成员所使用的关键字 | 派生类对基类的继承方式 | 派生类对基类成员访问权限 |
| --- | --- | --- |
| public | public | 相当于使用了public关键字 |
| public | protected | 相当于使用了protected关键字 |
| public | private | 相当于使用了private关键字 |
| protected | public | 相当于使用了protected关键字 |
| protected | protected | 相当于使用了protected关键字 |
| protected | private | 相当于使用了private关键字 |
| private | public | 不可访问 |
| private | protected | 不可访问 |
| private | private | 不可访问 |

### 结论：

从表可以看出，无论使用哪种方式生成的派生类，其成员函数都可以访问基类中除了 private 成员以外的其它成员。

如果希望基类成员能够被派生类所访问，而同时又不希望被类外部的其它函数直接访问，那么应该使用的基类成员限定符是 protected，而不是 private。

### 小结：

- 1. 对于以 public 方式生成的派生类，在基类中使用 public 和 protected 关键字限定的成员，在派生类中仍相当于使用了 public 和 protected 关键字；
- 2. 对于以 protected 方式生成的派生类，在基类中使用 public 和 protected 关键字限定的成员，在派生类中都相当于使用了 protected 关键字；
- 3. 而对于以 private 方式生成的派生类，它们都相当于使用了 private 关键字。

派生类并不是对基类中的所有成员都可以无条件访问的。

- 对（3）来说，无论使用的是哪种继承方式，在基类中以 private 关键字进行限定的成员在派生类中都是不可以访问的。

## 2. 派生类的构造函数和析构函数

### （1）派生类的构造函数

基类往往有构造函数和析构函数，前面讲过，派生类的数据成员包含基类的数据成员和派生类中新定义的数据成员。因此在派生类的构造函数中，除了要初始化派生类自己定义的数据成员外，还要初始化基类中的数据成员。而派生类只能通过调用基类的构造函数来初始化基类的数据成员。

定义派生类构造函数的一般格式如下：

`<派生类名>（<参数表>）：<基类的构造函数>(<实参>)`

例如：

```
class dynmem
{
public:
    //......
    dynmem(int eps,int wsize);//基类构造函数
    //......
};
class relmem:dynmem
{
    //......
public:
    relmem(int nmas,int eps,int wsize);
    //声明时不用后缀基类的构造函数
};
relmem::relmem(int nmas,int eps,int wsize):dynmem(eps, wsize)
{
    //定义派生类的构造函数时后缀上基类的构造函数
    //......
}
```

在定义对象时，构造函数的执行顺序是先基类，再所有对象成员，后自己（派生类本身）。

### （2）派生类的析构函数

```
{ cout<<"the destructor of class teacher!\n" }
};
main()
{
    student d1;
    teacher d2;
    return 1;
}
```

运行结果为：

```
the constructor of class person!
the constructor of class student!
the constructor of class person!
the constructor of class teacher!
the destructor of class teacher!
the destructor of class person!
the destructor of class student!
the destructor of class person!
```

## 二. 多重继承

### 1. 基本内容

前面我们讲到过，当一个派生类只有一个基类时，我们称这种继承方式为单一继承。一般情况下，我们还允许一个派生类具有多于一个的基类，这种派生方式被称为多重继承（multiple inheritance）。多重继承是单一继承的自然扩展，两者有同一性，又有特殊性。图 2-2 给出了一个多重继承的示例。在这个示例中，类 Software 由两个类 OperatingSystem 和 Application 派生，而类 ComputerSystem 又由类 Software 和另一个类 Hardware 派生。

![](img/3b4669cf00b2833fe526284506f3f342_180_0.png)

图 2-2 多重继承结构

- (1) 一个类的基类可以多于一个，这种继承叫多继承。
- (2) 一个类由多个类派生的一般形式为：

```
class 派生类名：<access>基类1，<access>基类2，……，<access>基类n
{
```
