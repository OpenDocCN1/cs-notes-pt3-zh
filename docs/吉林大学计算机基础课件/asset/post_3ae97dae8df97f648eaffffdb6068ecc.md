
## 6.1.1   C语言简介

- C语言是一种通用的、过程式的编程语言，广泛用于系统与应用软件的开发。具有高效、灵活、功能丰富、表达力强和较高的移植性等特点，在程序员中备受青睐。
- C语言是由UNIX的研制者Dennis Ritchie于1970年在B语言的基础上发展和完善起来的。目前，C语言编译器普遍存在于各种不同的操作系统中，例如UNIX、MS-DOS、Microsoft Windows、Linux等。C语言的设计影响了许多后来的编程语言，例如C++、Objective-C、Java、C#等。

## C语言的主要特点

- （1） C语言是一种结构化程序设计语言
- （2） 效率高
- （3） 可移植性好
- （4） 简洁紧凑、灵活方便
- （5） 运算符丰富
- （6） 数据类型丰富

## 快速测试

- 1. C语言的发明者是谁？是哪一年发明的？
- 2. Java的发明者是谁？是哪一年发明的？
- 3. C语言的标准目前有哪些？
- 4. C语言与Java、C++之间的关系如何？

## 6.2 面向过程的程序设计

- “面向过程”是一种以过程为中心的编程思想。面向过程的程序设计是把程序看成是完成一定功能的过程，是对现实世界的运动状态的模拟。
- 程序是通过对数据进行一系列的加工而实现，程序设计包括组织数据（设计数据结构）和对数据结构进行加工的过程（设计算法），即：算法＋数据结构＝程序。

## 例6.1 计算给定半径的圆面积

```
#include <stdio.h>

#define PI 3.1415926

double caluArea(int radius) //求圆的面积，radius是半径
{
    double area; //定义变量area保存面积
    area = PI * radius * radius;
    return area; //返回面积
}
```

## 主函数

```
int main(void) //主函数
{
    int radius; //定义整型变量radius

    printf("radius:");
    scanf("%d", &radius);   //输入radius的值
    printf("area=%f\n", caluArea(area)); //调用caluArea求圆的面积

    return 0;
}
```

## 编辑、编译、链接、运行过程图示

![](img/60882d3e569e0db30f34a44fdc73ab49_307_0.png)

## 例6.2 在一个有序表中查找指定值x

```
#include <stdio.h>
#define N 6
int main(void) {
    int v[N] = { 8, 14, 30, 45, 67, 89 }; //用一维数组v存放有序表
    int low = 0, high = N - 1, mid;    //low和high分别表示查找的上下界

    int x = 30;  //待查找的元素
    while (low <= high) {
        mid = (low + high) / 2;
        if (x < v[mid])
            high = mid - 1;  // 在前半部分查找
        else if (x > v[mid])
            low = mid + 1;   // 在后半部分查找
        else
            break;
    }
```

## 例6.2（续）

```
if (low <= high)
    printf("found in %d:\n", mid); //输出找到的位置
else
    printf("No found!\n"); //输出未找到的信息

return 0;
}
```

## 快速测试

- 1. C语言程序中必须包含的函数是什么？
- 2. 函数caluArea的功能是什么？编写计算球的表面积和体积的函数caluArea和caluVolume。
- 3. 折半查找的基本思想是什么？若将例6.2中的x改为21，程序的运行结果是什么？

## 6.3 面向对象的程序设计

- (1) 世界由各种对象组成，任何事物都是对象，是某个对象类的实例；复杂的对象可由比较简单的对象以某种方式组成；
- (2) 所有对象划分成各种对象类，每个对象类都定义了一组方法；
- (3) 对象之间只有互相传递消息的联系；
- (4) 对象类按“类”、“子类”与“父类”的关系构成层次结构的系统。面向对象的方法可概括为： OO = Object + Classes + Inheritance + Communication with messages

## 例6.3 计算给定半径的圆面积

```
package ch1;

public class Circle {
    double PI = 3.1415926;
    private int radius;

    Circle(int r) {
        radius = r;
    }
}
```

## 例6.3 (续)

```
double getArea() // 求圆的面积, radius是半径 {
 double area; // 定义变量area保存面积
 area = PI * radius * radius;
 return area; // 返回面积
 }
```

```
public static void main(String[] argv) {
 Circle cl = new Circle(6);
 System.out.printf("area=%f\n", cl.getArea());
 }
```

## 例6.4 类的继承实例： Human类与 Student类

```
package ch1;

class Human {
  String name;
  String id;

  Human(String name0, String id0) {
    name = name0;
    id = id0;
  }
}
```

## 例6.4（续）

```
void print() {
    System.out.printf("Name:%s, Id:%s\n", name, id);
}
};

class Student extends Human {
    String sid;

    Student(String name0, String id0, String sp0) {
        super(name0, id0);
        sid = sp0;
    }
```

## 例6.4（续）

```java
void print() {
    super.print();
    System.out.printf("Sid:%s\n", sid);
}

public static void main(String args[]) {
    Student s1 = new Student("zhang san", "123", "S2012");
    s1.print();
}
```

## 6.4 软件工程概念

- 软件工程是研究和应用如何以系统性的、规范化的、可定量的过程化方法去开发和维护软件，以及如何把经过时间考验而证明正确的管理技术和当前能够得到的最好的技术方法结合起来的学科。它涉及到程序设计语言、数据库、软件开发工具、系统平台、标准、设计模式等方面。
- 软件工程师是对用软件创造软件的人们的统称，软件工程师按照所处的领域不同可以分为系统分析员、软件设计师、系统架构师、程序员、测试员等等。

## 6.4.2 软件工程的基本原理

- (1) 用分阶段的生命周期计划严格管理
- (2) 坚持阶段评审
- (3) 执行严格的产品控制
- (4) 采纳现代程序设计技术
- (5) 结果应能清楚地审查
- (6) 开发小组的人员应少而精
- (7) 承认不断改进软件工程实践的必要性

软件工程目标：在给定成本、进度的前提下，开发出具有可修改性、有效性、可靠性、可理解性、可维护性、可重用性、可适应性、可移植性、可追踪性和可互操作性并且满足用户需求的软件产品。追求这些目标有助于提高软件产品的质量和开发效率，减少维护的困难。

## 作业

- 习题6
  - 一、 选择题
  - 二、 判断题
  - 三、 填充题
  - 四、 用C语言或Java编程
  - 五、 简答题
