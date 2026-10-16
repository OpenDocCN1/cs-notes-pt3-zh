# 名字空间里的运算符示例

```
namespace std{
    class ostream{
        char* p = "Hello";
        ostream& operator<<(const char*);
    };
    extern ostream cout;
    class string{
        // ...
    };
    ostream operator<<(ostream&, const string&);
}
```

# 一元运算符的解析方式

+   - 考虑一元运算符@，如果x的类型为X而y的类型为Y，x@y将按照如下方式解析
+     - 若@类是，查询作为X的成员函数或者Y的某个基类的成员函数的operator@()声明
+     - 在函数@()的环境中查询operator@的声明
+     - 若在名空间内里定义了@，在全局查询operator@的声明
+   - 当查询到operator@重载时，按照重载规则处理
+   - 一元运算符的解析方式与二义类似

# 11.3 一个复数类型

+   - 我们希望实现一个复数类，可以进行如下操作
+   - 此外，还希望提供一些运算符，例如一些比较、<<输出等

```
void f()
{
    complex a=complex(1,2);
    complex b=3;
    complex c=a+2.3;
    complex d=2+b;
    complex e=-b-c;
    b=c*2*c;
}
```

# 11.3.1 成员运算符和非成员符

+   - 作者喜欢让尽量少的函数能直接去操作对象的表示，因此，作者只允许本类去定义那些本质上需要修改第一个参数值的运算符，如十=，而像+这样基于参数的值简单产生新值的运算符，则在类之外利用基本运算符来定义