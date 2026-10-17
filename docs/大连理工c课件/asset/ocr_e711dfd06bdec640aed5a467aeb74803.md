# # 第3章 类与对象

# ## 3.5 拷贝构造函数

Point p1("home",1.0,2.0),p2("school",3.0),p3;
Point p4=p1 ;

对象空间

p4

x

1.0

y

2.0

flag

0

name

p1

x

1.0

y

2.0

flag

1

name

p2

x

1.0

y

2.0

flag

1

name

p3

x

0.0

y

0.0

flag

1

name

堆 空间

h
o
m
e
\0

s
c
h
o
o
1
\0

n
o
n
a
m
e
\0

大连理工大学院

类的成员函数空间

Point

Point(char \*,double,double)

Point(Point &)

~Point()

disp()