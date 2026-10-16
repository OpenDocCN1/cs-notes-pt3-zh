# 10.4.2 字符文件输入/输出流

+   在向文件中写数据或从文件中读数据时采用字符方式处理。

+   1、FileReader类
+   - 功能：读取字符文件，使用默认字符编码和默认字符缓冲区大小。
+   - 构造方法：
+     - FileReader(File file):创建一个从给定File对象中读取数据的字符文件输入流对象。
+     - FileReader(String fileName):创建一个从以fileName文件名指定的文件中读取数据的对象。