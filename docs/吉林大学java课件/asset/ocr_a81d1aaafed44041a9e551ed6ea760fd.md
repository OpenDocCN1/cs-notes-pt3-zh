# DataOutputStream类的常用方法

| No | 方法 | 类型 | 描述 |
|---|---|---|---|
| 1 | public DataOutputStream(OutputStream out) | 构造 | 实例化对象 |
| 2 | public final void writeInt(int v) throws IOException | 普通 | 将一个int值以4-byte值形式写入基础输出流中 |
| 3 | public final void writeDouble(double v) throws IOException | 普通 | 写入一个double类型，该值以8-byte值形式写入基础输出流中 |
| 4 | public final void writeChars(String s) throws IOException | 普通 | 将一个字符串写入到输出流之中 |
| 5 | public final void writeChar(int v) throws IOException | 普通 | 将一个字符写入到输出流之中 |