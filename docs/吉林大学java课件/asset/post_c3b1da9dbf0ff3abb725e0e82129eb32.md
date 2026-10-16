
## JAVA IO
—— 对象序列化

## 本章目标

- 掌握对象序列化的作用
- 掌握Serializable接口的作用
- 可以使用ObjectOutputStream进行对象序列化操作
- 可以使用ObjectInputStream进行对象的反序列化操作
- 掌握Externalizable接口的作用及与Serializable接口的实现区别
- 掌握transient关键字的作用

## 对象序列化

- 对象序列化，就是把一个对象变为二进制的数据流的一种方法，通过对象序列化可以方便的实现对象的传输或存储。

![](img/b706331eacf49a62651c2c9b2de81ca5_642_0.png)

- 如果一个类的对象想被序列化，则对象所在的类必须实现 java.io.Serializable接口。此接口定义如下：

```
public interface Serializable{}
```

## 定义可序列化的类

```
package org.lxh.demo12.serdemo;
import java.io.Serializable;
public class Person implements Serializable {    // 此类的对象可以被序列化
    private String name;    // 声明name属性
    private int age;        // 声明age属性
    public Person(String name, int age) {    // 通过构造函数设置属性内容
        this.name = name;
        this.age = age;
    }
    public String toString() {    // 覆盖toString()方法
        return "姓名: " + this.name + "; 年龄: " + this.age;
    }
}
```

## 对象的序列化和反序列化

- ✧ 要想完成对象的输入或输出，还必须依靠对象输出流（ObjectOutputStream）和对象输入流（ObjectInputStream）
- ✧ 使用对象输出流输出序列化对象的步骤，有时也称为序列化，而使用对象输入流读入对象的过程，有时也称为反序列化

![](img/b706331eacf49a62651c2c9b2de81ca5_644_0.png)

## serialVersionUID

序列化时为了保持版本的兼容性，即在版本升级时反序列化仍保持对象的唯一性。有两种生成方式：

- 一个是默认的1L，比如： private static final long serialVersionUID = 1L;
- 一个是根据类名、接口名、成员方法及属性等来生成一个64位的哈希字段，比如： private static final long serialVersionUID = xxxxL;

## 对象输出流： ObjectOutputStream

- 一个对象如果要想进行输出，则必须使用ObjectOutputStream类，此类定义如下：

```
public class ObjectOutputStream extends OutputStream implements ObjectOutput, ObjectStreamConstants
```

- 此类的常用方法如下

| No. | 方法或常量 | 类型 | 描述 |
|---|---|---|---|
| 1 | public ObjectOutputStream(OutputStream out) throws IOException | 构造 | 传入输出的对象 |
| 2 | public final void writeObject(Object obj) throws IOException | 普通 | 输出对象 |

此类的使用形式与PrintStream非常的相似，在实例化时也需要传入一个 OutputStream的子类对象，之后根据传入的OutputStream子类的对象不同，输出的位置也不同。

## 将Person类的对象保存在文件之中

```
package org.lxh.demo12.serdemo;
import java.io.File;
import java.io.FileOutputStream;
import java.io.ObjectOutputStream;
import java.io.OutputStream;
public class SerDemo01 {
    public static void main(String[] args) throws Exception {
        File f = new File("D:" + File.separator + "test.txt");
        ObjectOutputStream oos = null;
        OutputStream out = new FileOutputStream(f);            // 文件输出流
        oos = new ObjectOutputStream(out);                     // 为对象输出流实例化
        oos.writeObject(new Person("张三", 30));              // 保存对象到文件
        oos.close();                                           // 关闭输出
    }
}
```

## 对象输入流： ObjectInputStream

- 使用ObjectInputStream可以直接把被序列化好的对象反序列化回来。
- ObjectInputStream的定义如下：

```
public class ObjectInputStream extends InputStream implements ObjectInput, ObjectStreamConstants
```

- 此类的常用方法如下：

| No. | 方法或常量 | 类型 | 描述 |
|---|---|---|---|
| 1 | public ObjectInputStream(InputStream in) throws IOException | 构造 | 构造输入对象 |
| 2 | public final Object readObject() throws IOException, ClassNotFoundException | 普通 | 从指定位置读取对象 |

- 此类也是InputStream的子类，与PrintStream类的使用类似，此类同样需要接收InputStream类的实例才可以实例化。

## 从文件中将Person对象反序列化

```
package org.lxh.demo12.serdemo;
import java.io.File;
import java.io.FileInputStream;
import java.io.InputStream;
import java.io.ObjectInputStream;
public class SerDemo02 {
    public static void main(String[] args) throws Exception {
        File f = new File("D:" + File.separator + "test.txt");
        ObjectInputStream ois = null;
        InputStream input = new FileInputStream(f);        // 文件输入流
        ois = new ObjectInputStream(input);                // 为对象输出流实例化
        Object obj = ois.readObject();                     // 读取对象
        ois.close();                                       // 关闭输出
        System.out.println(obj);
    }
}
```

## Externalizable接口

被Serializable接口声明的类其对象的内容都将被序列化，如果现在用户希望可以自己指定序列化的内容，则可以让一个类实现Externalizable接口，此接口定义如下：

```
public interface Externalizable extends Serializable {
    public void writeExternal(ObjectOutput out) throws IOException;
    public void readExternal(ObjectInput in) throws IOException, ClassNotFoundException;
}
```
