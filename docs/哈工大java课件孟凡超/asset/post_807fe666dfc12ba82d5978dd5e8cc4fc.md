
## 使用Eclipse开发Java应用程序

步骤5(创建Java项目): 选择 “File” >“New” >“Project” 菜单，打开 “New Project” 窗口。在窗口下方的项目列表中单击 “Java”前面的 “+”号，展开该项目，单击选中 “Java Project”。

步骤6: 单击 “Next” 按钮，打开 “Create a Java Project” 窗口。在 “Project name” 编辑框中输入项目名称，如 “example”。

![](img/ca8bdf2cb3b7905fc97ee695aef3ed57_33_0.png)

![](img/ca8bdf2cb3b7905fc97ee695aef3ed57_33_1.png)

步骤7：单击 “Next” 按钮，进入 “Java Settings” 窗口。单击 “Finish” 按钮，在打开的 “Open Associated Perspective?” 对话框中单击 “Yes” 按钮，表示在创建Java项目后打开Java相关视图。

![](img/ca8bdf2cb3b7905fc97ee695aef3ed57_34_0.png)

## 使用Eclipse开发Java应用程序

## 使用Eclipse创建Java程序

步骤1：启动Eclipse，在窗口左侧的包资源管理器中单击 chapter_1，即选中要在其中创建Java程序的包。选择 “File” >“New” >“Class” 菜单，打开 “New Java Class” 窗口。在 “Name” 编辑框中输入 “HelloWorld”，选中 public static void main (String[] args) 复选框（表示创建的类中包含main方法）。

![](img/ca8bdf2cb3b7905fc97ee695aef3ed57_36_0.png)

步骤2：单击“完成”按钮，回到Eclipse主界面，此时“HelloWorld”类文件已经创建好，并且其中给出了一些简单的代码。

![](img/ca8bdf2cb3b7905fc97ee695aef3ed57_37_0.png)

步骤3： 在代码编辑区的main方法中输入代码。

```java
package chapter_1;

public class HelloWorld {

	/**
	 * @param args
	 */

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		// 输出提示信息
		System.out.println("打印main方法中的输入参数！");
		// 声明一个整型变量i，将其作为for循环控制变量
		// 以输出命令行中输入的字符串
		for (int i = 0; i < args.length; i++) {
			System.out.println(args[i]);
		}
	}
}
```

步骤4：为了给程序指定运行参数，可选择 “Run”>“Run Configurations” 菜单，打开 “Run Configurations” 对话框。在对话框右侧区域打开 “(x)=Arguments” 选项卡，在其中的编辑框中输入 “Hello World”作为程序运行参数。

![](img/ca8bdf2cb3b7905fc97ee695aef3ed57_39_0.png)

步骤5：依次单击 “Apply” 和 “Run” 按钮，编译和运行程序，系统将在主窗口右下方的 “控制台” 选项卡中输出程序运行结果。

![](img/ca8bdf2cb3b7905fc97ee695aef3ed57_40_0.png)

## Java程序设计

孟凡超

哈尔滨工业大学(威海)计算机科学与技术学院

mfc@hitwh.edu.cn

## 参考资料

- 1. 辛运帏, 饶一梅, 马素霞. Java程序设计(第二版). 清华大学出版社, 2006.

## 课程内容

- 第1章 概述
- 第2章 标识符和数据类型
- 第3章 表达式和流程控制语句
- 第4章 数组、向量和字符串
- 第5章 进一步讨论对象和类
- 第6章 Java语言中的异常
- 第7章 Java的图形用户界面设计
- 第8章 Swing组件
- 第9章 Java Applet
- 第10章 Java数据流
- 第11章 线程
- 第12章 网络功能

![](img/ca8bdf2cb3b7905fc97ee695aef3ed57_43_0.png)

## 第2章 标识符和数据类型

- Java的基本语法单位
- Java编码体例
- Java的基本数据类型
- 复合数据类型
- 类和对象的初步介绍

## 2.1 Java的基本语法单位

- package语句: 可以没有，如果有必须放在文件开始地方。
- import语句: 可以没有，也可以有多个。如果有import语句的话，必须放在所有类定义之前。
- public型的class定义: 每个文件中最多有一个。
- class定义: 每个文件中包含的类定义的个数没有限制。
- Interface定义: 每个文件中包含的接口定义个数没有限制。

## 2.1 Java的基本语法单位

### ■1 空白、注释及语句

空白：在Java程序中，换行符及回车都可以表示一行的结束，它们可以被看作是空白，另外，空格键、水平定位键(tab)亦是空白。为了增加程序可读性，Java程序元素之间可以插入任意数量空白，编译器忽略多余的空白。

(2)提倡的程序风格

### 口两种程序风格比较：

(1)不提倡的程序风格

```
/*
package example.Chapter_2;

/**
 * @author Fanchao Meng
 *
 */
public class Point {
int x,y;Point(int x1,int y1){x=x1;y=y1;} Point(){this(0,0);}
void moveto(int x1,int y1){x=x1;y=y1;}
```

```
/*
package example.Chapter_2;

/**
 * @author Fanchao Meng
 *
 */
public class Point {
    int x,y;            //点的x轴,y轴坐标
    Point(int x1,int y1){  //带参数的构造方法
        x=x1;
        y=y1;
    }
    Point(){            //不带参数的构造方法
        this(0,0);
    }
    void moveto(int x1,int y1){ //点移动到(x1,y1)
        x=x1;
        y=y1;
    }
}
```

## 2.1 Java的基本语法单位

注释：程序中适当地加入注释会增加程序可读性。注释不能插在一个标识符或关键字之中，即要保证程序中最基本元素的完整性。

### 三种注释方式

- (1) //在一行注释
- (2) /*一行或多行注释 */
- (3) /**文档注释 */

```
package example.Chapter_2;

/**
 * 点的定义
 * @author Fanchao Meng
 */
public class Point {
    int x, y;//点的x轴,y轴坐标
    /*
     * 带参数的构造方法
     */
    Point(int x1,int y1){
        x=x1;
        y=y1;
    }
    /*
     * 不带参数的构造方法
     */
    Point(){
        this(0,0);
    }
    /*
     * 点移动到 (x1,y1)
     */
    void moveto(int x1,int y1){
        /*将x1赋予x轴坐标，将y1赋予y轴坐标*/
        x=x1;
        y=y1;
    }
}
```

## 2.1 Java的基本语法单位

### 注释语句、分号和块

- 语句是Java中最小执行单位。一个语句可以写在连续的若干行内。
- 各语句间以分号 ";" 隔开。
- 花括号 "{" 和 "}" 之间包含的一系列语句称为语句块，简称块。语句块可以嵌套，即语句块中可以含有子语句块。
