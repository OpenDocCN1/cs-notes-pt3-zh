# # 12.1.3 预定义流

+   - Java程序自动导入java.lang包（定义了System类）。
+   - System 包含三个预定义的流变量：
+     in、out 和 err（定义成 public 和 static）
+   - System.out是标准输出流（默认是控制台）。
+   - System.in是标准输入流（默认是键盘）。
+   - System.err是标准错误流（默认是控制台）。
+   - 可以重定向到任何兼容的输入/输出设备。
+   - System.in 是inputStream的对象；System.out和System.err是PrintStream的对象。
+   - 都是字节流，尽管它们用来读写外设的字符。