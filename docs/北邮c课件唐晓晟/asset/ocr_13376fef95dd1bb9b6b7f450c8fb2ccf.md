# 15.4.2.1 静态和动态强制(casts)

dynamic_cast能从多态性的基类指针到某个派生类或者兄弟类，而static_cast不检查被强制的对象，所以它做不到这些

```
void g(Radio& r){
Receiver* prec = &r; // Receiver是Radio的常见基类
Radio* pr = static_cast<Radio*>(prec); // 可行，不检查
pr = dynamic_cast<Radio*>(prec); // 可行，运行时检查
Storable* ps = &r; // Storable是Radio的另一基类
pr = static_cast<Radio*>(ps); // 错误，不能跨基类强制
pr = dynamic_cast<Radio*>(ps); // 可行，运行时检查
}
```

# 静态和动态强制(casts)

dynamic_cast要求多态性的操作对象，这是因为在非多态对象里没有存储有关信息，而从一个对象触及到它可以作为基类对象的那些派生对象，需要这种信息

所以还存在一种static_cast进行的类层次结构的变化，这是因为在某些情况下互换的代价是动态_cast可以使用的那部分由，大都是C风格强制来保证合法性，常常造成潜在的错误

因此，尽量dynamic_cast有一些运行的开销，在所有可能的地方，还是应该去用更安全的dynamic_cast

# 静态和动态强制(casts)示例

编译器不能对void*所指向的存储提供任何保证，这意味着dynamic_cast不能从void*出发进行强制，因为它必须去查看对象，以确定其类型

这种情况下使用static_cast

dynamic_cast和static_cast都遵守const和访问控制规则

```
Radio* f(void* p){
Storable* ps = static_cast<Storable*>(p);
// 指针类型是！
return dynamic_cast<Radio*>(ps);
}
```

# 15.4.3 类对象的构造和析构

一个类对象并非简单地就是一块存储

类对象是通过其构造函数从“原始存储”中构建起来的，并通过其析构函数的执行使它重归于“原始存储”

构造是一个自下而上的过程，析构则自上而下

一个类对象也就是在它能够以构造或析构的意义上才称其为对象