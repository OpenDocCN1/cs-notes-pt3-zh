# 第3章 类与对象

# 3.5 拷贝构造函数

```
Point p1("home",1.0,2.0),p2("school",3.0),p3;
Point p4=p1;
```

![](bbox=[0.1, 0.3, 0.88, 0.99])

对象空间

p4：x 1.0，y 2.0，name 指向堆中的字符串“home”

p1：x 1.0，y 2.0，name 指向堆中的字符串“home”

p2：x 1.0，y 2.0，name 指向堆中的字符串“school”

p3：x 0.0，y 0.0，name 未初始化

类的成员函数空间

```
Point
Point(char *,double,double)
~Point()
disp()
```

堆空间

P4的name与p1的name相同