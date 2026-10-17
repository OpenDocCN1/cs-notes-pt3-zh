

## 例 P22

```java
/*
Demonstrate the for loop.
Call this file "ForTest.java".
*/
class ForTest {
    public static void main(String args[]) {
        int x;
        for(x = 0; x < 10; x = x + 1) // for(x = 0; x < 10; x++)
            System.out.println("This is x: " + x);
    }
}
```

## 2.5 使用程序块

- 可以将 2 个或 2 个以上的语句组成一组，这样的一组语句称为程序块（Codeblocks）。
- 程序块是通过将所属语句放在花括号中来实现。
- 它就成为一个逻辑单元，可以作为一个单独的语句来使用。

## 例 P24

```java
/*
Demonstrate a block of code.
Call this file "BlockTest.java"
*/
class BlockTest {
    public static void main(String args[]) {
        int x, y;
        y = 20;
        // the target of this loop is a block
        for(x = 0; x < 10; x++) {
            System.out.println("This is x: " + x);
            System.out.println("This is y: " + y);
            y = y - 2;
        }
    }
}
```

Ans:

This is X: 0
This is Y: 20
This is X: 1
This is Y: 18
This is X: 2
This is Y: 16
This is X: 3
This is Y: 14
This is X: 4
This is Y: 12
This is X: 5
This is Y: 10
This is X: 6
This is Y: 8
This is X: 7
This is Y: 6
This is X: 8
This is Y: 4
This is X: 9
This is Y: 2

![](img/489adce8323ca3a7b0e9fe701e6e665c_46_0.png)

## 2.6 基本词汇

### 2.6.1 空白分隔符（whitespace）

空白分隔符可以是空格，Tab 跳格键或是换行符。

### 2.6.2 标识符（identifiers）

标识符是赋给类、方法或是变量的名字。
一个标识符可以是大写和小写字母、数字、下划线、美元符号的任意顺序组合，但不能以一个数字开始。

## 基本词汇（续）

### 2.6.3 常量（literal）

100 98.6 'X' "This is a test"

### 2.6.4 注释（comments）

单行注释、多行注释、文档注释。

### 2.6.5 分隔符（separators）

| 分隔符 | 名称 | 用途 |
| :--- | :--- | :--- |
| () | 圆括号 | 在定义和调用方法时用来容纳参数表。在控制语句或强制类型转换组成的表达式中用来表示执行或计算的优先权。 |
| {} | 花括号、大括号 | 用来包括自动初始化的数组的值。也用来定义程序块、类、方法以及局部范围。 |
| [] | 方括号、中括号 | 用来声明数组的类型，也用来表示撤消对数组值的引用。 |
| ; | 分号 | 用来终止一个语句。 |
| ， | 逗号 | 在变量声明中，用于分隔变量表中的各个变量。在 for 控制语句中，用来将圆括号内的语句连接起来。 |
| . | 句号（点） | 用来将软件包的名字与它的子包或类分隔。也用来将引用变量与变量或方法分隔。 |

## 基本词汇（续）

## 2.6.6 Java 关键字：48 个保留关键字

abstract const finally int public this boolean continue float interface return throw break default for long short throws byte do goto native static transient Case double if new strictfp try Catch else implements package super void char extends import private switch volatile Class final instanceof protected synchronized while

Java 还有以下保留字：true，false，null。

## 2.6.7 Java 类库

作为一个整体，Java 是 Java 语言本身和它的标准类的组合体。

类库包含许多内置的方法，用以提供对诸如输入/输出（I/O）、字符串处理、网络、图形的支持。标准的类还提供对窗口输出的支持。

# 第一部分 Java 语言

# 第 03 章 数据类型、变量、数组

## 3.1 Java 语言是强类型语言

- Java 语言强类型语言。
- Java 的安全和健壮性部分来自于强类型语言。
- 每个变量有类型，每个表达式有类型，而且每种类型是严格定义的。
- 所有的数值传递，不管是直接的还是通过方法调用经由参数传过去的都要先进行类型相容性的检查。
- Java 编译器对所有的表达式和参数都要进行类型相容性的检查以保证类型是兼容的。
- 任何类型的不匹配都是错误的，在编译器完成编译以前，错误必须被改正。

## 3.3 整数类型

- Java 定义了 4 个整数类型：byte, short, int, long。
- Java 不支持无符号的整数。

| 类型 | 位数 | 范围 |
| :--- | :--- | :--- |
| 长整型 | 64 | -9,223,372,036,854,775,808 ~ 9,223,372,036,854,775,807 |
| 整型 | 32 | -2,147,483,648 ~ 2,147,483,647 |
| 短整型 | 16 | -32,768 ~ 32,767 |
| 字节型 | 8 | -128 ~ 127 |

## 3.3.1 字节型（byte）

- 有符号的 8 位类型。
- 数的范围是 -128～127。
- 从网络或文件处理数据流的时候，字节类型的变量特别有用。
- 处理未加工的二进制的数据时，它们也是有用的。
- 例如：byte b, c;

## 3.3.2 短整型（short）

- 有符号的 16 位类型。
- 数的范围是 -32,768 ~ 32,767。
- 可能是 Java 中使用得最少的类型。
- 例如：
  ```java
  short s;
  short t;
  ```

## 3.3.3 整型（int）

- 最常用的整数类型是 int。它是有符号的 32 位类型。
- 数的范围是 -2,147,483,648～2,147,483,647。
- 包含 byte，short，int 及字面量数字，有进行计算以前，所有表达式的类型被提升到 int。
- 整型是最通用并且有效的类型。

## 3.3.4 长整型（long）

- 有符号的 64 位类型
- 数的范围是 -9,223,372,036,854,775,808 ~ 9,223,372,036,854,775,807
- 对于那些整型不足以保存所要求的数值时是有用的。

## 例 P30

```java
// Compute distance light travels using long variables.
class Light {
    public static void main(String args[]) {
        int lightspeed;
        long days;
        long seconds;
        long distance;
        // approximate speed of light in miles per second
        lightspeed = 186000;
        days = 1000; // specify number of days here
        seconds = days * 24 * 60 * 60; // convert to seconds
        distance = lightspeed * seconds; // compute distance
        System.out.print("\n " + days);
        System.out.print(" days light will travel about ");
        System.out.println(distance + " miles.");
    }
}
```

![](img/489adce8323ca3a7b0e9fe701e6e665c_59_0.png)

