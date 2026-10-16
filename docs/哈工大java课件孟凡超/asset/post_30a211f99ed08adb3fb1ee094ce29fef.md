
## 10.2 基本字节数据流

![](img/ca8bdf2cb3b7905fc97ee695aef3ed57_324_0.png)

程序
(内存)

数据

write

输出流

file2.txt

```
import java.io.FileNotFoundException;
import java.io.FileOutputStream;
import java.io.IOException;

public class FileStream1 {

    /**
     * @param args
     */
    public static void main(String[] args) {
        // TODO Auto-generated method stub
        try{
            FileOutputStream out=new FileOutputStream("file2.txt");
            out.write('h');
            out.write('a');
            out.write('r');
            out.write('b');
            out.write('i');
            out.write('n');
            out.close();
        }catch(FileNotFoundException e){
            System.out.println("Error:cannot open file for waiting.");
        }catch(IOException e){
            System.out.println("Error:cannot write to file.");
        }
    }
}
```

### 过滤器数据流

### 缓冲区数据流

- ✓ 包括 **BufferedInputStream** 和 **BufferedOutputStream**，它们都是过滤器数据流，都是在数据流上增加了一个缓冲区。
- ✓ 当读写数据时，数据以 **块** 为单位先进入 **缓冲区**（块的大小可以进行设置），其后的读写操作则作用于缓冲区。
- ✓ 只有缓冲区满时，才会将数据送到输出流。一般在关闭一个缓冲区输出流之前，应使用 flush() 方法，强制输出剩余数据，以确保缓冲区内的所有数据全部写入输出流。
- ✓ 提供了对 mark()、reset()、skip() 等方法的支持。

![](img/ca8bdf2cb3b7905fc97ee695aef3ed57_326_0.png)

增加缓冲区流，减少访问硬盘的次数，提高效率！

```
public static void main(String[] args) {
    // TODO Auto-generated method stub
    try{
        FileInputStream in=new FileInputStream("file1.txt");
        InputStream bin=new BufferedInputStream(in);
        FileOutputStream out=new FileOutputStream("file2.txt");
        OutputStream bout=new BufferedOutputStream(out);
        int c;
        while((c=bin.read())!=-1){
            bout.write(c);
        }
        bout.flush();
        in.close();
        bin.close();
        out.close();
        bout.close();
    }catch(FileNotFoundException e){
        e.printStackTrace();
    }catch(IOException e){
        e.printStackTrace();
    }
}
```

### 数据数据流

- ✓ 文件流和缓冲区流的处理对象是字节或字节数组，利用数据输入输出流可以实现对文件的不同数据类型的读写。
- ✓ DataInputStream 和 DataOutputStream：一种较为高级的数据输入输出方式，除了字节和字节数组，还可以处理 int、float、boolean 等类型。
- ✓ 还可以用 readLine 方法读取一行信息。
- ✓ 创建方式：

```
FileInputStream in=new FileInputStream("file1.txt");
FileOutputStream out=new FileOutputStream("file2.txt");
DataInputStream din = new DataInputStream(in);
DataOutputStream dout = new DataOutputStream(out);
```

DataInputStream主要方法：

- byte readByte();
- long readLong();
- double readDouble();
- boolean readBoolean();
- String readUTF();
- int readInt();
- float readFloat();
- short readShort();
- char readChar();

DataOutputStream主要方法:
- void writeByte();
- void writeLong();
- void writeDouble();
- void writeBoolean();
- void writeUTF();
- void writeInt();
- void writeFloat();
- void writeShort();
- void writeChar();

### 数据数据流示例(2)

```java
DataInputStream in = new DataInputStream(
new FileInputStream("D:/java/Java2s.txt"));
double price;
int unit;
String desc;
double total = 0.0;
try {
while (true) {
price = in.readDouble();
in.readChar(); // throws out the tab
unit = in.readInt();
in.readChar(); // throws out the tab
desc = in.readline();
System.out.println( desc );
System.out.println( price );
System.out.println( unit );
total = total + unit * price;
System.out.println( total );
}
} catch (EOFException e) {
}
in.close();
```

### 管道数据流

- > 管道数据流主要用于线程间的通信。
- > 一个线程中的 PipedInputStream 对象从另一个线程中互补的 PipedOutputStream 对象中接收输入。
- > 类 PipedInputStream 必须和类 PipedOutputStream 一起使用，来建立一个通信通道。
- > 管道数据流必须同时具备可用的输入端和输出端。

创建 一个通信通道 (方法2):

```
PipedInputStream pis = new PipedInputStream();
PipedOutputStream pos = new PipedOutputStream(pis);
```

```
PipedOutputStream pos = new PipedOutputStream();
PipedInputStream pis = new PipedInputStream(pos);
```
