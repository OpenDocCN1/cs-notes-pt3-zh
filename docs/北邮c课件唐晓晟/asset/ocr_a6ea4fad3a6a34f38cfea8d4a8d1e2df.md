# 14.2.1 派生的异常

+   - 由于异常的类层次结构，很多情况下，异常抽象代码块只针对基类(而不是特定的子类)异常进行捕捉

+   - 捕捉和命名异常的语法等同于函数接受参数语法

# 派生的异常示例

```
class Matherr {
    //...
    virtual void debug_print() const {
        cerr << "Math error";
    }
};

class Int_overflow:public Matherr {
    const char* op;
    int a1, a2;
public:
    Int_overflow(const char* p,int a,int b){
        op = p; a1 = a; a2 = b; }
    virtual void debug_print() const {
        cerr << op << a1 << a2; }
};

void f() {
    try { g(); }
    catch(Matherr m){...}
}
```

调用f()的客户端实际上是一个Int_overflow。这意味着即使Matherr构造函数，也能捕捉Int_overflow所提供的附加信息将是不可访问的

若要避免附加信息丢失，catch后面声明中声明为Matherr的引用或指针者将

# 14.2.2 多个异常的组合

+   - 并不是每个异常都具有树形结构，也常有一个异常同时属于两个组的情形，如下，这样的一个Netfile_err异常能够被处理网络的异常捕捉，也能被处理文件系统异常的函数捕捉

+   - 对于错误处理的这种非层次性结构的组织形式很复杂，奇则用户或许根本意识不到自己捕捉了某个异常

```
class Netfile_err:public Network_err, public File_system_err
{...};
```

# 14.3 捕捉异常

```
void f() {
    try {
        throw E();
    }
    catch(H()) {
        //如何进行到这里？
    }
}
```

此外，还可以用于捕捉异常的类是异常的公共基类。异常进行到能捕捉到的异常

+   1. 如果H和E是同类型的类
+   2. 如果H和E是公共基类
+   3. 如果H和E是无关类，[1]或[2]对派生引用或指针类型成立
+   4. 如果H和E是无关类，[1]或[2]对H所引用的类型成立