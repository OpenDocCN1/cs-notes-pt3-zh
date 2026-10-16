# 间接示例

+   - 对于等概率的一般使用一元参数队伍的某些重用开发意义较大，有了`p->`共同层级，即可安全地完成对象的成员访问。
+   - 对于用户自己定义的`->`运算符，不保证这些关系，但若必要，并中间也提供这些部分指针。

```
class Ptr_to_Y{
    Y* p;
public:
    Y& operator=(){ return p;}
    Y& operator*(){ return *p;}
    Y& operator[](int i){ return p[i];}
};
```

# 11.11 增量和减量

+   - 一旦归定义`class Ptr_to_T`，一旦对指针的增量和减量进行重载，就可以像使用内置指针一样使用它。

```
class Ptr_to_T{
    T* p;
public:
    Ptr_to_T(T* p, T* v, int s);
    Ptr_to_T& operator++(); // 前缀
    Ptr_to_T& operator++(int); // 后缀
    Ptr_to_T& operator--(); // 前缀
    Ptr_to_T& operator--(int); // 后缀
    T& operator*();
};
```

# 增量和减量示例

```
void f1(T a)
{
    T y[200];
    T* p=&v[0];
    *p--;
    *p=a;
    // p越界，没有捕捉到
    ++p;
    *p=a; // ok
}

void f2(T a)
{
    T y[200];
    Ptr_to_T p(&y[0], y, 200);
    p--; // p.operator--(0);
    p=a;
    // p.operator*() = a;
    ++p;
    *p=a; // ok
}
```

# 11.12 一个字符串类

+   - 一个更实际的String类版本
+   - 提供了一种语言义、字符读写操作、检查和不检查的访问、流I/O、用字符串字面量作为文字量、相等和拼接运算符，字符串表示为C风格的、用0结束的字符数组，并利用引用计数尽可能地减少复制