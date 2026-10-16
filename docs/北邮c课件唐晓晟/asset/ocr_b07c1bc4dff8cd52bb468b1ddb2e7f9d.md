# 8.2.9.3 名字空间是开放的

可以通过多个名字空间声明给它加入名字

```
namespace A{ int f(); } //A中没有g()
namespace A{ int g(); } //A中既有f()和g()
void A::f() { ... }
```

注意，当定义一个名字空间中已经声明过的成员时，安全的方法是采用语法形式 A::语法格式

```
void A::f() { ... }
//Error:A没有g()
//不要使用如下方式
namespace A{ void g() {...}; } //这个声明会引入一个前置声明f()，而不是 //实现已经声明过的f()请注意，编译器不检查
```

# 8.3 异常

当一个程序是由一些相互分离的模块组成时，特别是当这些模块来自某些独立开发的库时，错误处理的工作就需要分成两个相互独立的部分

+   - 一方报告那些无法在局部解决的错误
+   - 另一方处理那些在其他地方被查出来的错误

异常(exception)机制是C++中用于将错误报告与错误处理分开的手段

# 8.3.1 抛出和捕捉

异常概念是为了帮助处理错误的报告

基本思想是：如果函数发现了一个自己无法处理的问题，它就抛出(throw)一个异常，希望它的(直接或间接)调用者能够处理这个问题。如果一个函数想处理某个问题，它就可以说明自己要捕捉(catch)用于报告这种问题的异常

# 异常处理示例

```
struct Range_error{
 int i;
 Range_error(int ii)
 :i(ii){}
};
char_to_char(int i)
{
 if(i<numeric_limits<char>::min()
 || i>numeric_limits<char>::max())i
 throw Range_error(i);
 return i;
}
```

```
void g(int i)
{
 try {
 char c = to_char(i);
 ...
 } catch(Range_error x){
 cerr << "oops\n";
 cerr << x.i << endl;
 }
}
```

其中catch(...){...}为异常处理者，它只能作为try语句作为底层的块之，或或者接下来有一个后续处理之行