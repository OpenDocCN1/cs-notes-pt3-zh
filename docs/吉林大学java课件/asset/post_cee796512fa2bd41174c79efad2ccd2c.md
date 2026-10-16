
## JAVA标识符和关键字

## 本章目标
- 掌握public class与class声明的区别
- 掌握Java中的注释使用
- 掌握Java中的标识符的命名规则
- 了解Java中的关键字
- 掌握变量及常量的声明

## 一个简单的Java程序

```
public class TestJava {
    public static void main(String[] args) {    // Java操作的一个简单
    范例，输出和乘方
        int num = 10;                           // 定义整型变量
        num = 30;                               // 修改变量内容
        System.out.println("num的内容是: " + num);    // 输出内容
        System.out.println("num * num = " + num * num);// 输出乘方
    }
}
```

## 使用public class和class声明的区别
- public class文件名必须与类名称一致
- class文件名可以与类名称不一致

![](img/b706331eacf49a62651c2c9b2de81ca5_3_0.png)

## Java程序的注释

在java中根据功能的不同，注释主要分为以下三种：
- 单行注释
- 多行注释
- 文档注释

## Java中的标识符
- Java中的包、类、方法、参数和变量的名字，可由任意顺序的大小写字母、数字、下划线（_）和美元符号（$）组成，但标识符不能以数字开头，不能是Java中的保留关键字。
- 合法的标识符:
  - yourname、yourname_lxh、li_yourname、$yourname
- 非法的标识符:
  - class、67.9、Hello LiXingHua

## Java中的关键字

| abstract | boolean | break | byte | case | catch | char |
|---|---|---|---|---|---|---|
| class | continue | default | do | double | else | extends |
| false | final | finally | float | for | if | implements |
| import | instanceof | int | interface | long | native | new |
| null | package | private | protected | public | return | short |
| static | synchronized | super | this | throw | throws | transient |
| true | try | void | volatile | while | assert | enum |

### 关键字说明：
- 1. 在Java中goto和const没有任何的意义
- 2. assert是在JDK 1.4之后增加进来的
- 3. enum是在JDK 1.5之后增加进来的

## 变量和常量
- 变量：
  - 将内存中的某个内存块保留下来以供程序使用，里面的内容是可变的
- 常量：
  - 一个数字就表示常量、常量内容是不会改变的

## 下一章内容

## Java 基本数据类型

![](img/b706331eacf49a62651c2c9b2de81ca5_8_0.png)

## Java基础程序设计
—— Java数据类型

## 本章目标
- 掌握Java数据类型的划分
- 掌握Java中的八种基本数据类型
- 掌握数据类型间的相互转换

## Java数据类型划分

数据类型

基本数据类型

引用数据类型

数值型

整数类型 (byte, short, int, long)

浮点类型 (float, double)

字符型 (char)

布尔型 (boolean)

类 (class)

接口 (interface)

数组

## 引用数据类型
- 数组Array，类 class，接口interface属于引用类型。
- 引用类型的变量是所引用的对象的内存地址。

```
class MyDate {
    private int day = 1;
    private int month = 1;
    private int year = 2000;
    public MyDate( int day, int month, int year) { ... }
    public void print() { ... }
}
public class TestMyDate {
    public static void main( String[] args) {
        MyDate my_birth = new MyDate( 22, 7, 1964);    }
}
```

## 引用数据类型（*reference type*）
- ☆ 创建一个类对象：
- ☆ `MyDate my_birth = new MyDate(22, 7, 1964);`

![](img/b706331eacf49a62651c2c9b2de81ca5_13_0.png)

## 引用数据类型 (reference type)

两个引用变量的赋值将会产生如下结果：

```
int x = 7;
int y = x;
MyDate s = new MyDate(22, 7, 1964);
MyDate t = s;
```

两个变量指向同一个对象：

![](img/b706331eacf49a62651c2c9b2de81ca5_14_0.png)

## Java基本数据类型

| No. | 数据类型 | 大小/位 | 可表示的数据范围 |
|---|---|---|---|
| 1 | long（长整数） | 64 | -9223372036854775808 ~ 9223372036854775807 |
| 2 | int（整数） | 32 | -2147483648 ~ 2147483647 |
| 3 | short（短整数） | 16 | -32768~32767 |
| 4 | byte（位） | 8 | -128 ~ 127 |
| 5 | char（字符） | 2 | 0 ~ 255 |
| 6 | float（单精度） | 32 | -3.4E38（-3.4×10³⁸） ~ 3.4E38（3.4×10³⁸） |
| 7 | double（双精度） | 64 | -1.7E308（-1.7×10³⁰⁸） ~ 1.7E308（1.7×10³⁰⁸） |

## 整数类型

当数据不带有小数或分数时，即可以声明为整数变量，如3，-147等即为整数。Java中，整数数据类型可以分为long、int、short及byte四种：long为64位，也就是8个字节（bytes），可表示范围为-9223372036854775808到9223372036854775807；int为32位，也就是4个字节，表示范围为-2147483648到2147483647；若是数据值的范围在-32768到32767之间时，可以声明为short（短整数）类型；若是数据值更小，在-128到127之间时，可以声明为byte类型以节省内存空间。举例来说，想声明一个短整型变量sum时，可以在程序中做出如下的声明：

```
short sum ; // 声明sum为短整型
```

## 数据过长

```
class DataDemo01 {
    public static void main(String[] args) {
        int num = 9999999999999999999999 ;
        // 定义整型变量，错误，超出长度范围
    }
}
```

## 数据的溢出
- 当整数的数据大小超出了可以表示的范围，而程序中又没有做数值范围的检查时，这个整型变量所输出的值将发生紊乱，且不是预期的运行结果。

## 将整型的最大值加1和加2

```java
class DataDemo02 {
	public static void main(String[] args) {
		int max = Integer.MAX_VALUE;
		// 得到整型的最大值
		System.out.println("整型的最大值: " + max);
		// 输出最大值
		System.out.println("整型最大值 + 1:" + (max + 1));
		// 最大值加1
		System.out.println("整型最大值 + 2:" + (max + 2));
		// 最大值加2
	}
}
```

![](img/b706331eacf49a62651c2c9b2de81ca5_19_0.png)
