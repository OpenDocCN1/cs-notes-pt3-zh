# RandomAccessFile类的常用操作方法

| No. | 方法 | 类型 | 描述 |
|---|---|---|---|
| 1 | public RandomAccessFile(File file,String mode) throws FileNotFoundException | 构造 | 接收File类的对象，指定操作路径，但是在设置时需要设置模式；"r": 只读、"w": 只写、"rw": 读写 |
| 2 | public RandomAccessFile(String name,String mode) throws FileNotFoundException | 构造 | 不再使用File类对象表示文件，而是直接输入了一个固定的文件路径 |
| 3 | public void close() throws IOException | 普通 | 关闭操作 |
| 4 | public int read(byte[]) b) throws IOException | 普通 | 将内容读取到一个byte数组之中 |
| 5 | public final byte readByte() throws IOException | 普通 | 读取一个字节 |
| 6 | public final int readInt() throws IOException | 普通 | 从文件中读取整数数据 |
| 7 | public void seek(long pos) throws IOException | 普通 | 设置读指针的位置 |
| 8 | public final void writeBytes(String s) throws IOException | 普通 | 将一个字符串写入到文件之中，按字节的方式处理。 |
| 9 | public final void writeInt(int v) throws IOException | 普通 | 将一个int型数据写入文件，长度为4位 |
| 10 | public int skipBytes(int n) throws IOException | 普通 | 指针跳过多少个字节 |