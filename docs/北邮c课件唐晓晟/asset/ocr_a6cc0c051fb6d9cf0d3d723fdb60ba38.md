# 示例

```
void* operator new(size_t size) // 某类new的实现
{
    for(;;){
        if(void* p = malloc(size)) return p; // 申请内存
        if(_new_handler == 0) throw bad_alloc(); // 无处理器
        _new_handler(); // 正常情况，如果我们找不到内存
    }               // 就会抛出一个异常。否则就先循环
    // _new_handler()是new无法申请到内存时，系统内定的处理
    // 器。当然，也可以由自己的函数替代之
    // set_new_handler(&my_new_handler);
    // 每个C++实现都保证内存是存在的，在任何情况下都抛出
    // bad_alloc。当然，全部根据情形而可能发生的
```

# 示例

```
void my_new_handler();
void f(){
    void(*oldh)() = set_new_handler(&my_new_handler);
    try{
        // ...
    }
    catch(bad_alloc){
        // ...
    }
    catch(...){
        set_new_handler(oldh); // 重新处理器
        throw; // 重新抛出
    }
    set_new_handler(oldh); // 置空处理器
    // 也可利用异常中初始化和技术使避免使用catch语句
```

# 14.4.6 构造函数里的异常

# 异常也是从构造函数里报告出错的向题提供一个解决方案，构造函数无法返回一个独立的值提供用程序检查，传统的解决方法有

+   - 返回一个处于错误状态的对象，相信用户无法检查出来
+   - 设置一个后备变量，指出创建失败，相信用户能去检查这个变量
+   - 在构造函数中本身就初始化，依靠用户在第一次使用对象前查看是否有个初始化函数
+   - 将对象标记为“未完成初始化”，让这个构造函数用的下一个构造函数去完成实际的初始化工作，并且在它在初始化失败时报告错误

# 构造函数里的异常

# 异常处理机制使构造失败的信息能从构造函数内部传出来

```
class Vector{
public:
    class Size{};
    enum {max = 32000};
    Vector(int sz){
        if(sz<0 || sz>max) throw Size();
    } // ...
};

Vector* f(int i){
    try{
        Vector* p = new Vector(i);
        return p;
    }
    catch(Vector::Size){
        // 处理异常
    }
}
```