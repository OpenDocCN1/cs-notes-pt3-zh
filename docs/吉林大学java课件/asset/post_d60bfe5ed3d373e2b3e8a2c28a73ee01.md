
# ◆String类

```
String s1 = "hello";
String s2 = "world";
String s3 = "hello";
...
```

Code

Constant
常量池

"hello"
"world"
...

s1
s2
s3
...

Stack
栈

用引号创建的对象" hello"和" world"是存储在常量池当中的，s1和s3指向的是同一块内存区域。因此，当我们用等号比较时，可以得到true的结果。

# String类

Code

```
s1 = new String ("hello");
s2 = new String ("hello");
...
```

Heap
堆

Stack
栈

![](img/b706331eacf49a62651c2c9b2de81ca5_153_0.png)

# 面向对象（基础）
—— String类的常用方法

# 本章目标

- 掌握String类中的常用方法
- 了解API文档的查找方法

# String类中的常用方法（1）

| No. | 方法定义 | 类型 | 描述 |
|---|---|---|---|
| 1 | public String(char[] value) | 构造 | 直接将一个字符数组变为一个字符串 |
| 2 | public String(char[] value,int offset,int count) | 构造 | 将一个指定范围的字符数组变为字符串 |
| 3 | public String(byte[] bytes) | 构造 | 将一个byte数组全部变为字符串 |
| 4 | public String(byte[] bytes,int offset,int length) | 构造 | 将指定范围的byte数组变为字符串 |
| 5 | public char[] toCharArray() | 普通 | 将一个字符串变为字符数组 |
| 6 | public char charAt(int index) | 普通 | 从一个字符串中取出指定位置的字符 |
| 7 | public byte[] getBytes() | 普通 | 将一个字符串变为byte数组 |
| 8 | public int length() | 普通 | 取得字符串长度 |
| 9 | public int indexOf(String str) | 普通 | 从头开始查找指定的字符串位置 |
| 10 | public int indexOf(String str,int fromIndex) | 普通 | 从指定位置开始查找指定的字符串位置 |
| 11 | public String trim() | 普通 | 清除左右两端的空格 |

# String类中的常用方法（2）

| No. | 方法定义 | 类型 | 描述 |
|---|---|---|---|
| 12 | public String substring(int beginIndex) | 普通 | 从指定位置开始，一直直到尾进行字符串的截取 |
| 13 | public String substring(int begin,int end) | 普通 | 指定截取字符串的开始点和结束点 |
| 14 | public String[] split(String regex) | 普通 | 按照指定的字符串对字符串进行拆分（*） |
| 15 | public String toUpperCase() | 普通 | 将一个字符串全部变为大写字母 |
| 16 | public String toLowerCase() | 普通 | 将一个字符串全部变为小写字母 |
| 17 | public boolean startsWith(String prefix) | 普通 | 判断是否以指定的字符串开头 |
| 18 | public boolean endsWith(String suffix) | 普通 | 判断是否以指定的字符串结尾 |
| 19 | public boolean equals (String str) | 普通 | 判断两个字符串内容是否相等 |
| 20 | public boolean equalsIgnoreCase(String str) | 普通 | 不区分大小写比较两个字符串是否相等 |
| 21 | public String replaceAll(String regex,String replacement) | 普通 | 字符串替换（*） |

# 面向对象（基础）
—— 引用传递及其应用

# 本章目标

- □ 掌握三种引用传递的操作范例
- □ 掌握引用传递的应用

# 引用传递（1）

```
class Demo {
    int temp = 30;                // 此处为了访问方便，属性暂不封装
}
public class RefDemo01{
    public static void main(String[] args) {
        Demo d1 = new Demo();
        d1.temp = 50;
        System.out.println("fun() 方法调用之前: " + d1.temp);
        fun(d1);
        System.out.println("fun() 方法调用之后: " + d1.temp);
    }
    public static void fun(Demo d2) {          // 此处的方法由主方法直接调用
        d2.temp = 1000;
    }
}
```

# 引用传递（2）

```
public class RefDemo02 {
    public static void main(String[] args) {
        String str1 = new String("hello"); // 实例化字符串对象
        System.out.println("fun()方法调用之前: " + str1);
        fun(str1);                           // 调用fun()方法
        System.out.println("fun()方法调用之后: " + str1);
    }
    public static void fun(String str2) {   // 此处的方法由主方法直接调用
        str2 = new String("MLDN");          // 修改字符串内容
    }
}
```

# 引用传递（2） —— 内存分析

String str1 = "hello" ;

fun(str1)

str2 = "MLDN"

fun()方法执行完后断开连接

![](img/b706331eacf49a62651c2c9b2de81ca5_163_0.png)

![](img/b706331eacf49a62651c2c9b2de81ca5_163_1.png)

![](img/b706331eacf49a62651c2c9b2de81ca5_163_2.png)

![](img/b706331eacf49a62651c2c9b2de81ca5_163_3.png)

# 引用传递（3）

```
class Demo {
    String temp =new String("hello"); // 此处为了访问方便，属性暂不封装
}
public class RefDemo03 {
    public static void main(String[] args) {
        Demo d1 = new Demo();                    // 实例化对象
        d1.temp = new String( "world");         // 修改对象中的temp属性
        System.out.println("fun() 方法调用之前：" + d1.temp);
        fun(d1);                                 // 调用fun() 方法
        System.out.println("fun() 方法调用之后：" + d1.temp);
    }
    public static void fun(Demo d2) {           // 此处的方法由主方法直接调用
        d2.temp =new String( "MLDN");           // 修改属性的内容
    }
}
```

# 引用传递（3）——内存分析

Demo d1 = new Demo();

d1.temp = "world";

fun(d1);

fun()方法执行完后断开连接

![](img/b706331eacf49a62651c2c9b2de81ca5_165_0.png)
