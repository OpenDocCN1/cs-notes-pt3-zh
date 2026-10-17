

## 字符串

为了使用方便Java提供了String类型。

### 字符串变量的声明和初始化：

String 变量名；变量名=new String();

或

String 字符串变量 = new String（）；

例如：

String s=new String();

## 字符串赋值

可以为字符串变量赋一个字符串常量，也可以将一个字符串变量或表达式的值赋给字符串变量。

```java
s="Chinese people";
s2=s1;
s3="a lot of"+s2;
```

结果s2的值为 “Chinese people” ， s3的值为 “a lot of Chinese people” 。其中运算符 “+” 的作用是将前后的两个字符串连接起来

## 字符串的输出

字符串可以通过println()或print()语句输出。

例如，以下的语句序列为字符串变量s赋值并输出其值：

```java
s="All the world";
System.out.println(s);
```

输出结果为：

```
All the world
```

## 例一字符串应用

```java
public class StringUse
{
    public static void main(String[] args)
    {String s1, s2;
        s1=new String("Students should ");
        s2=new String();
        s2="study hard.";
        System.out.print(s1);
        System.out.println(s2);
        s2="learn english, too";
        System.out.print(s1);
        System.out.println(s2);
        s2=s1+s2;
        System.out.println(s2);}}
```

该程序的运行结果如下：

Students should study hard.

Students should learn english, too

Students should learn english, too

## 字符串操作

Java中通过String类来使用字符串
String类用很多成员方法来对字符串进行操作。如： 字符串访问、比较和转换等。

- length(): 返回字符串的长度。
- charAt(int index): 返回字符串中第index个字符 。
- indexOf(int ch): 返回字符串中字符ch第1次出现的位置。
- indexOf(String str, int index): 返回值是在该字符串中，从第index个位置开始，子字符串str第1次出现的位置。
- subString (int index1, int index2): 返回值是在该字符串中，从第index1个位置开始，到第index2-1个位置结束的子字符串。

将int，long，float，double，boolean等基本类型数据转换为String类型的方法是：

```java
String.valueOf(基本类型数据)
```

将字符串型数据转换为其他基本类型的方法及实例

| 方法 | 返回值类型 | 返回值 |
|---|---|---|
| Boolean.getBoolean("false") | boolean | false |
| Integer.parseInt("123") | int | 123 |
| Long.parseLong("375") | long | 375 |
| Float.parseFloat("345.23") | float | 345.23 |
| Double.parseDouble("67892.34") | double | 67892.34 |

- 字符串数组——多个字符串组成
  要表示一组字符串可以用字符串数组来实现。

```java
String str=new String[4];

str[0]="Chinese";
str[1]="English";
str[2]="Tianjin";
str[3]="Chongqing";
```

有什么特点？

# 第六章

# 类和对象

Class and Object

## 6.1 类和对象概述

- 面向对象的基本概念：
  - 面向对象技术中，将客观世界中的一个事物作为一个对象看待。每个事物都有自己的属性和行为
  - 从程序设计的角度，事物的属性可以用变量描述，行为用方法描述。
    - 类：定义属性和行为的模板
    - 对象是类的实例，对象与类的关系就像变量和数据类型的关系一样

## 对象与类

简单地说：
对象是表示现实世界中某个具体的事物；
类是对对象的抽象描述。

张二

将对象抽象为类

对类进行实例化

类(CLASS)，如：
“Man class”

## Java的类

- 面向对象的程序设计认为：程序由对象组成。
- 程序中的每个对象有自己的属性和能够执行的操作
- 只关心对象能够完成的操作，不必关注实现功能的过程
  - For Example： 用户买车

## Java的类

- Java的所有程序代码都属于某个类的内部
- Java的类分为两个部分
  - Java类库——由Java提供的大量的、可供用户调用的各种类的各种方法（我们可以使用的）
  - 用户编写的类（**我们需要学习的**）

# Java的类

Java类库——我们已经使用过的……

- String
- Math
- JOptionPane
- Scanner

## Java类库

### Math——数学类库

- 为用户处理数学问题提供方法（函数）
- 例如：
  - `Math.PI`
  - `Math.sin(double a)`
  - `Math.sqrt(double a)`
  - `Math.abs(int/long/float/double a)`
  - ……

- 在Math库中，有程序处理需要的各种数学（方法）函数

## 自定义类——用户编写程序

- 用户程序从类开始
- 一个用户程序可以有多个类
- 其中有且只有一个类中，有类的main()方法
- 每一个类可以有多个方法
- 不同的类之间的方法可以互相调用，除了main()方法

## 类的声明

```
[修饰符] class 类名 [extends 父类名] [implements 接口名列表]
{
    类的成员变量声明;
    类的方法声明;
}
```

这里，[]中的可以省略  
因此，一般的类声明格式为：

```
[修饰符] class 类名
```

## 例6-1 定义一个二维平面上点的类

```java
class Point {
private int x,y;
public void setPoint(int a,int b) {
x=a;
y=b;
}
public int getX() {
return x;
}
public int getY() {
return y;
}
public String toString() {
return "["+x+","+y+"]";
}
}
```

类名：Point

类变量成员：x，y

类的方法（1）：setPoint

类的方法（2）：getX取X坐标

类的方法（3）：getY 取Y坐标

类的方法（4）：toString 获取变量的字符串

