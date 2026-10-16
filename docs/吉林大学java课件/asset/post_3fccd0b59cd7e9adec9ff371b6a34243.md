
## JAVA IO
—— Scanner

## 本章目标
- 掌握Scanner类的作用
- 使用Scanner接收输入数据

## Scanner简介
在JDK 1.5之后JAVA提供了专门的输入数据类，此类可以完成BufferedReader类的功能。也可以方便的对输入数据进行验证。此类存放在java.util包中。

| No. | 方法或常量 | 类型 | 描述 |
|---|---|---|---|
| 1 | `public Scanner(File source) throws FileNotFoundException` | 构造 | 从文件中接收内容 |
| 2 | `public Scanner(InputStream source)` | 构造 | 从指定的字节输入流中接收内容 |
| 3 | `public boolean hasNext(Pattern pattern)` | 普通 | 判断输入的数据是否符合指定的正则标准 |
| 4 | `public boolean hasNextInt()` | 普通 | 判断输入的是否是整数 |
| 5 | `public boolean hasNextFloat()` | 普通 | 判断输入的是否是小数 |
| 6 | `public String next()` | 普通 | 接收内容 |
| 7 | `public String next(Pattern pattern)` | 普通 | 接收内容，进行正则验证 |
| 8 | `public int nextInt()` | 普通 | 接收数字 |
| 9 | `public float nextFloat()` | 普通 | 接收小数 |
| 10 | `public Scanner useDelimiter(String pattern)` | 普通 | 设置读取的分隔符 |

## 使用Scanner类输入数据
- 实例操作一：实现基本的数据输入
- 实例操作二：实现日期格式的数据输入

## 实例操作一：实现基本的数据输入
```
package org.lxh.demo12.scannerdemo;
import java.util.Scanner;
public class ScannerDemo01 {
    public static void main(String[] args) {
        Scanner scan = new Scanner(System.in);    // 从键盘接收数据
        System.out.print("输入数据: ");
        String str = scan.next();
        System.out.println("输入的数据为: "+str);
    }
}
```

## 修改输入数据的分隔符
- 在Scanner类中默认的读取分隔符是“ ”，所以如果要想输入有空格数据的时候就需要修改分隔符，使用如下的语句：
- scan.useDelimiter("\n");

## 输入int、float
```
package org.lxh.demo12.scannerdemo;
import java.util.Scanner;
public class ScannerDemo03 {
    public static void main(String[] args) {
        Scanner scan = new Scanner(System.in);  // 从键盘接收数据
        int i = 0 ;
        float f = 0.0f ;
        System.out.print("输入整数: ");
        if(scan.hasNextInt()){                      // 判断输入的是整数
            i = scan.nextInt() ;                    // 接收整数
            System.out.println("整数数据: " + i) ;
        }else{                                      // 输入错误的信息
            System.out.println("输入的不是整数！") ;
        }
        System.out.print("输入小数: ");
        if(scan.hasNextFloat()){                    // 判断输入的是小数
            f = scan.nextFloat() ;                  // 接收小数
            System.out.println("小数数据: " + f) ;
        }else{                                      // 输入错误的信息
            System.out.println("输入的不是小数！") ;
        }
    }
}
```

## 实例操作二：实现日期格式的数据输入
```
package org.lxh.demo12.scannerdemo;
import java.text.ParseException;
import java.text.SimpleDateFormat;
import java.util.Date;
import java.util.Scanner;
public class ScannerDemo04 {
    public static void main(String[] args) {
        Scanner scan = new Scanner(System.in);  // 从键盘接收数据
        System.out.print("输入日期 (yyyy-MM-dd) : ");
        String str = null;
        Date date = null;
        if (scan.hasNext("^\\d{4}-\\d{2}-\\d{2}$")) { // 判断输入格式是否是日期
            str = scan.next("^\\d{4}-\\d{2}-\\d{2}$");          // 接收日期格式的字符串
            try {
                // 转换或日期
                date = new SimpleDateFormat("yyyy-MM-dd").parse(str) ;
            } catch (ParseException e) {
                e.printStackTrace();
            }
        }else{
            System.out.println("输入的日期格式错误！");
        }
        System.out.println(date);
    }
}
```

## JAVA IO
—— 数据操作流

## 数据操作流
- 在io包中，提供了两个与平台无关的数据操作流：
- 数据输出流（DataOutputStream）
- 数据输入流（DataInputStream）

通常数据输出流会按照一定的格式将数据输出，再通过数据输入流按照一定的格式将数据读入

例如：有以下的定单数据

| 商品名称 | 商品价格 | 商品数量 |
|---|---|---|
| 衬衣 | 98.3 | 3 |
| 手套 | 30.3 | 2 |
| 围巾 | 50.5 | 1 |

## DataOutputStream
- DataOutputStream是OutputStream的子类，此类的定义如下：
- public class DataOutputStream extends FilterOutputStream implements DataOutput
- 此类继承自FilterOutputStream类（FilterOutputStream是OutputStream的子类）同时实现了DataOutput接口，在DataOutput接口定义了一系列的写入各种数据的方法。

## DataOutputStream类的常用方法
| No | 方法 | 类型 | 描述 |
|---|---|---|---|
| 1 | public DataOutputStream(OutputStream out) | 构造 | 实例化对象 |
| 2 | public final void writeInt(int v) throws IOException | 普通 | 将一个int值以4-byte值形式写入基础输出流中 |
| 3 | public final void writeDouble(double v) throws IOException | 普通 | 写入一个double类型，该值以8-byte值形式写入基础输出流中 |
| 4 | public final void writeChars(String s) throws IOException | 普通 | 将一个字符串写入到输出流之中 |
| 5 | public final void writeChar(int v) throws IOException | 普通 | 将一个字符写入到输出流之中 |
