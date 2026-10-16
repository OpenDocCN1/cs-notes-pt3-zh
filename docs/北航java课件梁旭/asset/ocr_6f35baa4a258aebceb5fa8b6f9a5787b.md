# 10.3.3 字符过滤流

+   2、BufferedWriter类
+   - 功能：将文本写入字符输出流，缓冲各个字符，从而提供单个字符、数组和字符串的高效写入。
+   - 构造方法：
+     BufferedWriter(Writer out):创建一个使用默认大小输出缓冲区的缓冲字符输出流。
+     BufferedWriter(Writer out, int sz):创建一个使用给定大小输出缓冲区的缓冲字符输出流。
+   - 常用方法：
+     newLine():写入一个行分隔符。行分隔符字符串由系统属性 line.separator 定义，并且不一定是单个新行 ('\n') 符。