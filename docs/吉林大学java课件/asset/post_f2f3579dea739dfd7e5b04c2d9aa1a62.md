
## 使用循环的方式读取内容

```
package org.lxh.demo12.chariodemo;
import java.io.File;
import java.io.FileReader;
import java.io.Reader;
public class ReaderDemo02 {
    public static void main(String[] args) throws Exception {        // 异常抛出去，不处理
        // 第1步：使用File类找到一个文件
        File f = new File("d:" + File.separator + "test.txt");        // 声明File对象
        // 第2步：通过子类实例化父类对象
        Reader reader = null;                                        // 准备好一个输入的对象
        reader = new FileReader(f);                                  // 通过对象多态性，进行实例化
        // 第3步：进行读操作
        int len = 0;                                                 // 用于记录读取的数据个数
        char b[] = new char[1024];                                   // 所有的内容读到此数组之中
        int temp = 0;                                                // 接收读取的每一个内容
        while ((temp = reader.read()) != -1) {
            // 将每次的读取内容给temp变量，如果temp的值不是-1，则表示文件没有读完
            b[len] = (char) temp;
            len++;
        }
        // 第4步：关闭输入流
        reader.close();                                              // 关闭输入流
        System.out.println("内容为: " + new String(b, 0, len));
    }
}
```

## 字节流与字符流的区别

字节流在操作的时候本身是不会用到缓冲区（内存）的，是与文件本身直接操作的，而字符流在操作的时候是使用到缓冲区的。

![](img/b706331eacf49a62651c2c9b2de81ca5_580_0.png)

## 字节流与字符流的选择

- 所有的文件在硬盘或在传输的时候都是以字节的方式进行的，包括图片等都是按字节的方式存储的，而字符是只有在内存中才会形成，所以在开发中，字节流使用较为广泛。

## 范例：文件拷贝

在dos命令中存在一个文件的拷贝命令（copy），例如：现在要将D盘中的test.txt文件拷贝到D盘中的demo.txt文件，则只要在命令行中输入copy即可完成：

copy命令的语法格式如下：

```
copy 源文件 目标文件
```

```
Microsoft Windows XP [版本 5.1.2600]
(C) 版权所有 1985-2001 Microsoft Cor
C:\Documents and Settings\Administr
D:\>copy d:\test.txt d:\demo.txt
已复制 1 个文件。
```

```
D:\>copy d:\test.txt d:\demo.txt
系统找不到指定的文件。
```

## JAVA IO
—— 字节-字符转换流

## 本章目标

- □ 掌握OutputStreamWriter和InputStreamReader类的作用

## OutputStreamWriter和InputStreamReader

在整个IO包中，实际上就是分为字节流和字符流，但是除了这两个流之外，还存在了一组字节流-字符流的转换类。

- OutputStreamWriter: 是Writer的子类，将输出的字符流变为字节流，即：将一个字符流的输出对象变为字节流输出对象。
- InputStreamReader: 是Reader的子类，将输入的字节流变为字符流，即：将一个字节流的输入对象变为字符流的输入对象。

## 转换步骤

如果以文件操作为例，则在内存中的字符数据需要通过 OutputStreamWriter 变为字节流才能保存在文件之中，读取的时候需要将读入的字节流通过 InputStreamReader 变为字符流。

![](img/b706331eacf49a62651c2c9b2de81ca5_586_0.png)

## 将字节输出流变为字符输出流

```
package org.lxh.iodemo.changeiodemo;
import java.io.File;
import java.io.FileOutputStream;
import java.io.OutputStreamWriter;
import java.io.Writer;
public class OutputStreamWriterDemo01 {
    public static void main(String[] args) throws Exception { // 所有的异常抛出
        File f = new File("d:" + File.separator + "test.txt");
        Writer out = null;
        out = new OutputStreamWriter(new FileOutputStream(f)); // 字节流变为字符流
        out.write("hello world");        // 使用字符流输出
        out.close();
    }
}
```

![](img/b706331eacf49a62651c2c9b2de81ca5_587_0.png)

## 将字节输入流变为字符输入流

```
package org.lxh.iodemo.changeiodemo;
import java.io.File;
import java.io.FileInputStream;
import java.io.InputStreamReader;
import java.io.Reader;
public class InputStreamReaderDemo01 {
    public static void main(String[] args) throws Exception { // 所有的异常抛出
        File f = new File("d:" + File.separator + "test.txt");
        Reader reader = null;
        reader = new InputStreamReader(new FileInputStream(f)); // 将字节流变为字符流
        char c[] = new char[1024];
        int len = reader.read(c);
        reader.close();
        System.out.println(new String(c, 0, len));
    }
}
```

## JAVA IO
—— System对IO的支持

## 本章目标

- - 掌握System对IO的三种支持：
  - System.out
  - System.err
  - System.in
- 掌握System.out及System.err的区别
- 掌握输入、输出重定向

## System类

System类是一些与系统相关的属性和方法的集合，而且在System类中所有的属性都是静态的，要想引用这些属性和方法，直接使用System类调用即可。

| No. | 方法定义 | 类型 | 描述 |
|---|---|---|---|
| 1 | public static void exit(int status) | 普通 | 系统退出 |
| 2 | public static void gc() | 普通 | 运行垃圾收集机制，调用的是Runtime类中的gc方法 |
| 3 | public static long currentTimeMillis() | 普通 | 返回以毫秒为单位的当前时间 |
| 4 | public static void arraycopy(Object src,int srcPos,Object dest,int destPos,int length) | 普通 | 数组拷贝操作 |
| 5 | public static Properties getProperties() | 普通 | 取得当前的系统全部属性 |
| 6 | public static String getProperty(String key) | 普通 | 根据键值取得属性的具体内容 |
