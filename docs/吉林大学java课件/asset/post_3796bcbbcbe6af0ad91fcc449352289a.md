
## 最好的输入方式

- 最好的输入方式是将全部输入的数据暂时放到一块内存之中，之后一次性地从内存中读取出数据，这样所有数据只读了一次，则不会造成乱码，而且也不会受长度的限制。

![](img/b706331eacf49a62651c2c9b2de81ca5_604_0.png)

## 输入、输出重定向

从之前的操作中读者已经了解了System.out、System.err、System.in三个常量的作用，但是通过System类也可以改变System.in的输入流来源，以及System.out和System.err两个输出流的输出位置。

| No. | 方法或常量 | 类型 | 描述 |
|---|---|---|---|
| 1 | public static void setOut(PrintStream out) | 普通 | 重定向“标准”输出流 |
| 2 | public static void setErr(PrintStream err) | 普通 | 重定向“标准”错误输出流 |
| 3 | public static void setIn(InputStream in) | 普通 | 重定向“标准”输入流 |

## 为System.out输出重定向

```
package org.lxh.demo12.systemdemo;
import java.io.File;
import java.io.FileOutputStream;
import java.io.PrintStream;
public class SystemDemo06 {
    public static void main(String[] args) throws Exception { // 所有异常抛出
        System.setOut(new PrintStream(new FileOutputStream("d:" + File.separator + "red.txt"))); // System.out输出重定向
        System.out.print("www.mldnjava.cn");        // 输出时，不再向屏幕上输出
        System.out.println(", 李兴华");              // 而是向指定的重定向位置输出
    }
}
```

## 为用户保存错误信息

```
package org.lxh.demo12.systemdemo;
import java.io.File;
import java.io.FileNotFoundException;
import java.io.FileOutputStream;
import java.io.PrintStream;
public class SystemDemo07 {
    public static void main(String[] args) {
        String str = "hello";                     // 声明一个非数字的字符串
        try {
            System.out.println(Integer.parseInt(str));
        } catch (Exception e) {
            try {
                System.setOut(new PrintStream(new FileOutputStream("d:"+ File.separator + "err.log"))); // 输出重定位
            } catch (FileNotFoundException e1) {
                e1.printStackTrace();
            }
            System.out.println(e) ;                 // 输出错误，保存文件之中
        }
    }
}
```

## 为System.err输出重定向

```
package org.lxh.demo12.systemdemo;
import java.io.ByteArrayOutputStream;
import java.io.PrintStream;
public class SystemDemo08 {
    public static void main(String[] args) throws Exception { // 所有异常抛出
        ByteArrayOutputStream bos = null ;                     // 定义内存输出流
        bos = new ByteArrayOutputStream() ;                    // 实例化内存输出流
        System.setErr(new PrintStream(bos));                   // System.err输出重定向
        System.err.print("www.mldnjava.cn");                  // 错误输出时，不再向屏幕上输出
        System.err.println(", 李兴华");                        // 而是向内存的位置输出
        System.out.println(bos);                               // 打印错误信息
    }
}
```

## 设置System.in的输入重定向

```java
package org.lxh.demo12.systemdemo;
import java.io.File;
import java.io.FileInputStream;
import java.io.InputStream;

public class SystemDemo09 {

    public static void main(String[] args) throws Exception { // 所有异常抛出
        System.setIn(new FileInputStream("d:" + File.separator + "demo.txt")); // 设置输入重定向
        InputStream input = System.in; // 从文件接收数据
        byte b[] = new byte[1024]; // 开辟空间，接收数据
        int len = input.read(b); // 接收数据
        System.out.println("输入的内容为: " + new String(b, 0, len)); // 接收数据
        input.close(); // 关闭输入流
    }
```
```

## JAVA IO

—— BufferedReader

## 本章目标

- □ 掌握BufferedReader类的作用
- □ 掌握键盘输入的基本形式

## BufferedReader实例化

```
BufferedReader buf = null;

buf = new BufferedReader(new InputStreamReader(System.in));
```

字节输入流

将字符流放到字符缓冲区之中

将字节流变为字符流

## 键盘输入数据的标准格式

```
package org.lxh.demo12.buffdemo;
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
public class BufferedReaderDemo01 {
    public static void main(String[] args) {
        BufferedReader buf = null;
        buf = new BufferedReader(new InputStreamReader(System.in));
        String str = null;
        System.out.print("请输入内容：");
        try {
            str = buf.readLine();  // 读取内容
        } catch (IOException e) {
            e.printStackTrace();
        }
        System.out.println("输入的内容为：" + str);
    }
}
```
