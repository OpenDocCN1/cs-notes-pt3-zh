# 2.5 类和对象的初步介绍

# 口引用变量的赋值

Java把说明为class类型的变量看作是引用。

```
Point p1=new Point(10,20);
Point p2=p1;
p2.x=15;
p2.y=25;
System.out.println("p1.x="+p1.x+";  p1.y="+p1.y);
System.out.println("p2.x="+p1.x+";  p2.y="+p1.y);
```

p1 0X1abcdef 0X1abcdef p2
x 15
y 25

p1.x=15;p1.y=25
p2.x=15;p2.y=25