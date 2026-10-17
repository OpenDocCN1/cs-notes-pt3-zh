
## 浮点数

- 浮点数类型有2种表示形式：
  - 标准记数法
    - 由整数部分、小数点和小数部分组成
    - 如12.37
  - 科学记数法：由尾数、E或e及阶码组成
    - 也称为指数形式
    - 如2.5E4表示2.5×10⁴
  - 2种浮点数类型
    - float 单精度浮点数
    - double 双精度浮点数

## 取值范围及所占用的内存大小

| 浮点数类型 | 所占字节 | 取值范围 |
|---|---|---|
| float（单精度浮点数） | 4 | -3.4E38～3.4E38 |
| double（双精度浮点数） | 8 | -1.7E308～1.7E308 |

- 浮点数默认类型为double
- 表示浮点数为float型，加后缀F或f
  - 如34.5f

## 字符类型

- 字符类型：char
  - Unicode字符，1个字符占16位
- 字符类型数据表示方法
  - 单引号括起来的单个字符
  - 用Unicode码表示，前缀是“\u”
- Unicode字符集内的控制字符需要通过转义字符表示
  - 转义符 → 符号的意义被转换了
  - 转义后代表的是控制符

| 转义字符 | 功能 | Unicode码 |
|---|---|---|
| \b | 退格 | \u0008 |
| \t | 制表符 | \u0009 |
| \n | 换行 | \u000a |
| \f | 换页 | \u000c |
| \r | 回车 | \u000d |

## 字符串

- 字符串（String）
  - 由多个字符组成的字符序列
  - 字符串用双引号括起来
  - 如"green "

## 布尔类型

- 逻辑运算
  - 运算结果：真(true)或假(false)
- 布尔类型（boolean）
  - 表示逻辑运算，运算结果叫做“**布尔值**”
  - 运算结果，只有2个值：
    - true（真）
    - false（假）
    - 布尔值占1个字节

## Java数据基本类型表——小结

| 关键字 | 数据类型 | 所占字节 | 表示范围 |
|---|---|---|---|
| long | 长整型 | 8 | 2^31-1 ~ -2^31 |
| int | 整型 | 4 | -2147483648~ 2147483647 |
| short | 短整型 | 2 | -32768~32767 |
| byte | 位 | 1 | -128~127 |
| char | 字符 | 1 | 0~256 |
| boolean | 布尔 | 1 | true 或 false |
| float | 单精度 | 4 | -3.4E38~ 3.4E38 |
| double | 双精度 | 8 | -1.7E308~ 1.7E308 |

## 2 常量

### 常量

- 程序运行过程中其值始终保持不变的量
- 类似于数学中的“常数”

### Java中的常量类型

- 整型，如：26
- 浮点数型，如：47.3
- 字符型，如：'A'
- 布尔型，如：true
- 字符串型，如："student"

### 常量的这种表示方式称为直接常量

## 符号常量

- 标识符表示常量，称为符号常量
- 符号常量必须先声明，后使用
  - 声明关键字final，声明方式：
    `final [修饰符] 类型标识符 常量名 = （直接）常量;`
  - 修饰符是表示该常量使用范围的“权限修饰”：
    public，private，protected 或 缺省(不使用修饰符)
    - 如
      `final float PI=3.14159;    //PI是一个浮点常量`
      `final char SEX='M';    //SEX是一个字符常量`
      `final int MAX=100;    //MAX是一个整型常量`

## 符号常量的优点

1. 增加了程序的可读性
   - 从常量名可知常量的含义。

2. 增强了程序的可维护性
   - 只要在声明处修改常量的值，就自动修改了程序中所有地方所使用的常量值

## 3 变量

变量：程序运行中其值可以改变的量
变量必须先定义后使用
定义变量的格式：
[修饰符] 类型标识符 变量名[=常量];
例如：public int x=1;  // x为整型变量，初值为1
类型标识符：基本数据类型或引用数据类型
变量名必须符合标识符的规定→习惯小写
声明同类型的多个变量，用逗号分隔
若声明中包含“=常量”部分，系统将此常量作为变量的初始值

## Demo

以下是合法的变量声明
float x=25.4, y; // x、y为浮点型变量，x初值为25.4
char c; // c 为字符型变量
boolean flag1=true, flag2; // 布尔型变量
int n, m; // 整型变量
上例中
变量 x 和flag1 被赋予初始值
其它变量没有初始化

## 【例2-1】：使用整数型变量

```java
public class Integers {
    public static void main(String args[]) {
        int a=015; // 定义变量a，赋值八进制数
        int b=20; //十进制数
        int c=0x25; //十六进制数
        short x=30; //定义short型，十进制
        long y=123456L;
        System.out.println("a="+a); // 输出 a 的值
        System.out.println("b="+b); // 输出 b 的值
        System.out.println("c="+c); // 输出 c 的值
        System.out.println("x="+x); // 输出 x 的值
        System.out.println("y="+y); // 输出 y 的值
    }
}
```

## 【例2-1】结果

程序运行结果如下

a=13
b=20
c=37
x=30
y=123456

## 【例2-2】：使用浮点型变量

```java
public class Floats {
    public static void main(String args[]) {
        float a=35.45f;                 // 定义单精度变量a
        double b=3.56e18;               // 定义双精度变量b
        System.out.println("a="+a);    // 输出a
        System.out.println("b="+b);    // 输出b
    }
}
```

程序运行结果如下：

a=35.45

b=3.56E18

## 【例2-3】：使用字符类型变量

```java
public class Characters {
    public static void main(String args[]) {
        char ch1='a';        // 定义字符变量 ch1
        char ch2='B';         // 定义字符变量 ch2
        System.out.println("ch1="+ch1);  // 输出字符变量ch1
        System.out.println("ch2="+ch2);  // 输出字符变量ch2
    }
}
```

程序运行结果如下：
ch1=a
ch2=B

## 【例2-4】：使用字符串类型数据

```java
public class Samp2_5 {
    public static void main(String args[]) {
        String str1="abc"; // 定义字符串变量str1
        String str2="\n"; // 定义字符串变量str2
        String str3= "123"; // 定义字符串变量str3
        // 输出字符串变量时str1、 str2、 str3
        System.out.println("str1="+str1+str2+"str3="+str3);
    }
}
```
程序运行结果如下：
str1=abc
str3=123
