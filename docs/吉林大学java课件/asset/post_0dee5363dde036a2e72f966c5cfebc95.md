
# 不使用匿名内部类来实现抽象方法

```
abstract class Person {
    public abstract void eat();
}
class Child extends Person {
    public void eat() {
        System.out.println("eat something");
    }
}
public class Demo {
    public static void main(String[] args) {
        Person p = new Child();
        p.eat();
    }
}
```

运行结果：eat something
可以看到，我们用Child继承了Person类，然后实现了Child的一个实例，将其向上转型为Person类的引用

但是，如果此处的Child类只使用一次，那么将其编写为独立的一个类岂不是很麻烦？
这个时候就引入了匿名内部类

# 在接口上使用匿名内部类

```
interface Person {
    public void eat();
}

public class Demo {
    public static void main(String[] args) {
        Person p = new Person() {
            public void eat() {
                System.out.println("eat something");
            }
        };
        p.eat();
    }
}
```

运行结果： eat something

# 包及访问控制权限
—— 包的定义及导入

# 本章目标

- 了解多人开发的问题
- 掌握包的作用及定义
- 掌握包的导入语法及导入限制
- 了解系统常用包
- 掌握Java新特性——静态导入
- 掌握jar命令的使用

# 多人开发

- 在Java中，可以将一个大型项目中的类分别独立出来，分门别类地存到文件里，再将这些文件一起编译执行，如此的程序代码将更易于维护，

![](img/b706331eacf49a62651c2c9b2de81ca5_392_0.png)

# 多人开发的问题

如果有多个开发人员共同开发同一个项目的时候，则肯定会出现类名称相同的情况。那么这样一来就会比较麻烦

![](img/b706331eacf49a62651c2c9b2de81ca5_393_0.png)

# 包的定义

package是在使用多个类或接口时，为了避免名称重复而采用的一种措施，直接在程序中加入package关键字即可。

包的定义格式：

```
package 包名称.子包名称；
```

# 为程序打包

```
package org.lxh.demo08;    // 定义一个包
class Demo{                // 定义Demo类
    public String getInfo(){   // 返回信息
        return "Hello World!!!" ;
    }
}
public class PackageDemo01 {
    public static void main(String[] args) {
        System.out.println(new Demo().getInfo()) ;// 实例化本包对象
    }
}
```

程序编译： javac -d . PackageDemo01.java

# 访问包成员

- 可以使用 “.” 来访问包的成员。如：在包 “mypackage” 中有类Cal.class。要访问这个类可用如下格式：
mypackage.Cal;
- 如果要访问子包的成员也可以采用相同的方法。如：在包 “mypackage” 中有子包 “subpackage”，在subpackage 中有类Cal.class。要访问这个类可用如下格式：
mypackage.subpackage.Cal;

# PGM类

PGM（Portable GrayMap）是一种常见的灰度图像文件格式。本类提供了对PGM图像的读取、保存及像素访问等操作。

```
// PGM.h
#ifndef PGM_H
#define PGM_H

#include <string>

class PGM {
public:
    PGM();
    explicit PGM(const std::string& filename);
    ~PGM();
    
    bool read(const std::string& filename);
    bool write(const std::string& filename) const;
    
    int getWidth() const { return width_; }
    int getHeight() const { return height_; }
    int getMaxValue() const { return maxValue_; }
    unsigned char* getData() const { return data_; }
    
private:
    int width_;
    int height_;
    int maxValue_;
    unsigned char* data_;
};

#endif // PGM_H
```

read 函数负责解析PGM文件头（magic number、宽高、最大灰度值）以及读取像素数据；write 函数将图像数据按P2/P5格式写入文件。

# 关于“public class”与“class”声明类的完整补充

在本书的一开始，曾经为读者讲解过，如果一个类声明为public class则文件名称必须与类名称一致，而且在一个类中只能有一个public class，而如果使用class声明一个类，则文件名称可以与类名称不一致，但是执行的时候必须执行生成的class文件名称。除了这些之外，public class和class还在包的访问上有所限制，如果一个类只在本包中访问，不需要被外包访问，则直接声明成class即可，而如果一个类需要被外包访问，则必须声明为public class。

# 例子

```
package mypackage;//包的名称为mypackage
public class Calculate {
    int a;
    public Calculate()
    {a=10;}
    public double volume(double height,double  width,double depth)
    { return height*width*depth; }
    int add(int x,int y)
    { return x+y; }
    protected float mul(float x,float y)
    { return x*y; }
}
```

# 编译

- 保存成Calculate.java文件后，用-d选项编译此文件，就可以看到创建包名为mypackage的包了，在计算机上是以文件夹的形式展现在读者面前的。如下：
```
javac -d . Calculate.java
```

# 如何使用包中的类

```
import mypackage.Calculate;
class PackageDemo {
public static void main(String ags[]){
Calculate c=new Calculate();
System.out.print(c.volume(3f, 4f, 4));
//System.out.println(c.mul(3, 4));//非法
//System.out.println(c.add(5, 6)); //非法
}
}
```

注意：
1 该类的编译和运行需要设置环境变量classpath。
2 如何设置？ 设置Calculate类所属的包的所在子目录。

# 环境变量classpath设置

- 如果Calculate.class在d:\work\mypackage目录下，则classpath应设置为d:\work，而不应该是d:\work\mypackage。
- 如果Calculate属于mypackage.subpackage包，它在 d:\work\mypackage\subpackage目录下，那么classpath也应设置为 d:\work。
