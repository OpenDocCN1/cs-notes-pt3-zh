# System.in

+   - 标准输入流，InputStream类的对象。
+   - `int read()`方法：从键盘缓冲区读取一个字节数据，得到的返回值为一个int数据。返回值中的高字节都是0，低字节是读出的输入字符的编码，可判断是哪个字符。
+   - 可能产生IOException异常，需要try...catch语句处理。