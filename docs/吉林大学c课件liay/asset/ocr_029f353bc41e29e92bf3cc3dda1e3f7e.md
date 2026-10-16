```
```cpp
#define T float
//typedef float T;
void swap1(T &a,T &b)
{
    T temp=a;
    a=b;
    b=temp;
}
```
```

//固化的过死

//不能在调用时再给出类型

//宏替换仅能简化设计，而不能解决代码重用的问题。

//C++属于强类型语言，并不鼓励使用宏替换，