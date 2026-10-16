

## 14.3.1 重新抛出

- 在捕捉到了一个异常之后，很多情况下，处理者并不能完成对这个错误的全部处理，典型的方式是：该处理者能够局部做到的事情，然后再一次抛出这个异常，这将使得错误恢复动作分布在几个处理器里。
- 重新抛出用一个不带运算对象的throw语句。
- 重新抛出的异常就是当初捕捉到的那个异常，而不仅仅是异常处理器能够访问到的那个部分。

### 重新抛出示例

```
void h() {
    try { // 可能抛出Matherr的代码
        // ...
    }
    catch(Matherr){
        if(can_handle_it_completed){
            //处理Matherr
            return;
        }
        else{
            //完成这里做的事情
            throw;
        }
    }
}
```

## 14.3.2 捕捉所有异常

- 对于函数，省略号"..."表示"任何参数"。同样，catch(...)表示要捕捉所有异常。

```
void m() {
    try {
        // 一些代码
    }
    catch(...) { // 处理所有异常
        // 报告工作
        throw;
    }
}
```

### 14.3.2.1 处理器的顺序

- 派生异常可能被多于一个异常类型的处理器捕捉，因此，在try语句中处理器的排列顺序非常重要。

```
void f0() {
    try{
        ...
    }
    catch(std::ios_base::failure){
        //处理标准I/O信息
    }
    catch(std::exception& e){
        //处理所有标准异常
    }
    catch(...){
        //处理其他异常
    }
}
```

### 处理器的顺序

```
void f() {
    try {
        //...
    }
    catch(...) {
        //处理任何其他异常
    }
    catch(std::exception& e){
        //处理所有标准异常
    }
    catch(std::bad_cast){
        //处理dynamic_cast失败
    }
}
```

如果次序安排得不好，有些异常处理代码将永远不会运行。左例中，bad_cast部分将永远不被执行，即使catch(...)部分去掉也不行。

## 14.4 资源管理

- 当函数请求了某种资源（打开文件或者分配空间）时，一个很重要的问题就是需要正确释放这些资源。
- 但是如果程序在运行过程中产生了异常，就会导致程序的流程不是所希望那样，此时要特别注意资源问题。
- 异常产生时，实现会向上穿越堆栈去为某个异常查找对应处理器，叫做“堆栈回退”，此时，会对所有局部对象调用析构函数。

### 资源管理示例

```
void use_file(const char* fn) {
    FILE *f = fopen(fn,"r");
    //使用资源
    fclose(f);
}
//若在使用资源的过程中产生了异常，则fclose(f)将不会被调用，资源将不会被释放
```

```
void use_file(const char* fn) {
    FILE *f = fopen(fn,"r");
    try { //使用时
        ...
    }
    catch(...){
        fclose(f);
        throw;
    }
    fclose(f);
}
//一种解决办法，但是非常罗嗦
```

### 资源管理示例

考虑问题的一般形式：定义一个类File_ptr

```
class File_ptr {
    FILE* p;
public:
    File_ptr(const char* n, const char* a) { p = fopen(n, a); }
    File_ptr(FILE* pp) { p = pp; }
    ~File_ptr() { if(p) fclose(p); }
    operator FILE*() { return p; }
};
```

一般按照申请的顺序反向释放资源。也就是说，上述例子中只需要用`File_ptr f(fn,"r");`保护资源，析构函数就会被调用，资源就会被释放。

## 14.4.1 构造函数和析构函数的使用

- 利用局部对象管理资源的技术通常被称为“资源申请即初始化（resource acquisition is initialization）”。
- 只有在一个对象的构造函数执行完毕时，这个对象才被看作已经建立起来了。只有在此之后，异常产生时的堆栈回退才为该对象调用析构函数。
- 一个由子对象组成的对象的构造将一直持续到它所有的子对象都完成了构造。

### 示例

```
class X {
    File_ptr aa;
    Lock_ptr bb;
public:
    X(const char* x, const char* y)
        :aa(x,"rw"), // 申请x
         bb(y) // 申请y
    {}
};
```

考虑X，构造该类需要两种资源：文件x和锁y。这些资源都可能失效并抛出异常。若设计不当，程序容易出现异常。为此，可以使用两个（子对象）类来处理x、y。这保持程序结构不会改变也不会漏掉任何异常情况。若在创建aa()之后、bb()之前抛出了异常，aa()的析构函数将被调用，bb()则不会。

### 示例

```
class Y {
    int* p;
    void init();
public:
    Y(int s) {
        p = new int(s);
        init();
    }
    ~Y() { delete[] p; }
    //...
};
```

```
class Z {
    vector<int> p;
    void init();
public:
    Z(int s) : p(s) { init(); }
    //...
}; // 改造后的代码
```

// 若仅使用class Y那样的代码，可能导致内存泄漏

## 14.4.2 auto_ptr

- 标准库提供的auto_ptr支持“资源申请即初始化”的技术。
- 下例中，Rectangle和由pc所指向的Circle都将被删除，无论是否有异常被抛出。

```
void f(Point p1, Point p2, auto_ptr<Circle> pc, Shape* pb)
{
    auto_ptr<Shape> p(new Rectangle(p1,p2)); // 指向一个矩形
    auto_ptr<Shape> pbox(pb);
    p->rotate(45); // auto_ptr<Shape> 会释放 Shape* 指针
    //...
    if(in_a_mess) throw Mess();
} // 此时，p和pbox所指向的对象将被删除
```

### auto_ptr

- 为了获得这种所有权语义（ownership semantics），也常被称为破坏性复制语义（destructive copy semantic），auto_ptr具有与常规指针很不一样的复制语义：在将一个auto_ptr复制给另一个之后，原来的auto_ptr将不再指向任何东西。
- 因为复制auto_ptr将导致对它自身的修改，所以const auto_ptr就不能复制。

### auto_ptr的声明

```
template<class X> class std::auto_ptr {
public:
    typedef X element_type;
    explicit auto_ptr(X* p = 0) throw() { ptr=p; }
    ~auto_ptr() throw() { delete ptr; }
    auto_ptr(auto_ptr& a) throw() : ptr(a.ptr) { a.ptr=0; }
    template<class Y> auto_ptr(auto_ptr<Y>& a) throw() : ptr(a.ptr) { a.ptr=0; }
    auto_ptr& operator=(auto_ptr& a) throw() { delete ptr; ptr=a.ptr; a.ptr=0; }
    template<class Y> auto_ptr& operator=(auto_ptr<Y>& a) throw() { delete ptr; ptr=a.ptr; a.ptr=0; }
};
```

```
// 构造析构
X& operator*() const throw() { return *ptr; }
X* operator->() const throw() { return ptr; }
X* get() const throw() { return ptr; }
X* release() throw() { X* t=ptr; ptr=0; return t; }
// 放弃所有权
void reset(X* p=0) throw() { if (ptr!=p) { delete ptr; ptr=p; } }

auto_ptr(auto_ptr<X>& x) throw(); // auto_ptr复制
template<class Y> auto_ptr(auto_ptr<Y>& x) throw(); // 复制构造函数
template<class Y> operator auto_ptr<Y>() throw(); // auto_ptr隐式转换
```

### auto_ptr说明

- auto_ptr_ref的用途就是为普通auto_ptr实现破坏性复制语义，这使得const auto_ptr不可复制。
- 如果指针D*能转换到B*，那么这里的模板构造函数也能够将auto_ptr<D>转换到auto_ptr<B>。

