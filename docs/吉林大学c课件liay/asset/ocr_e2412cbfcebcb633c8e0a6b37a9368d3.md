# 16. 一个拷贝的例子

```
class Shape{
    public:
    //...
    virtual double area(){}
};
class Circle:public Shape{
    public:
    double area(){...}
    //...
};
class Triangle:public Shape{
    public:
    double area(){...}
    //...
};
//...
```

```
class Manage{
    shape *a[100];
    public:
    //...
}
```

要求完成Manage类的拷贝构造函数，实现深度拷贝；可以改动所有的类