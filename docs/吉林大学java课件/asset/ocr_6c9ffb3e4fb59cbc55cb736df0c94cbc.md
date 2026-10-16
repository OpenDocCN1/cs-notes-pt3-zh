# InputStream类的常用方法

| No. | 方法或常量 | 类型 | 描述 |
| --- | --- | --- | --- |
| 1 | public int available() throws IOException | 普通 | 可以取得输入文件的大小 |
| 2 | public void close() throws IOException | 普通 | 关闭输入流 |
| 3 | public abstract int read() throws IOException | 普通 | 读取内容，以数字的方式读取 |
| 4 | public int read(byte[] b) throws IOException | 普通 | 将内容读到byte数组之中，同时返回读入的个数 |