# # upcasting 带来的问题

```
class base  {
    //......
    int function();
};
class derived: public base {
    //......
    int function();
};
p0bj->function();  // 调用哪个函数？
```