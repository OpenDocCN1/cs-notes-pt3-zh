# OutputStream类的常用方法

| No. | 方法或常量 | 类型 | 描述 |
|---|---|---|---|
| 1 | public void close() throws IOException | 普通 | 关闭输出流 |
| 2 | public void flush() throws IOException | 普通 | 刷新缓冲区 |
| 3 | public void write(byte[] b) throws IOException | 普通 | 将一个byte数组写入数据流 |
| 4 | public void write(byte[] b,int off,int len) throws IOException | 普通 | 将一个指定范围的byte数组写入数据流 |
| 5 | public abstract void write(int b) throws IOException | 普通 | 将一个字节数据写入数据流 |

要想使用以上方法，必须使用子类实例化，此时使用FileOutputStream子类，此类的构造方法如下：

```
public FileOutputStream(File file) throws FileNotFoundException
```