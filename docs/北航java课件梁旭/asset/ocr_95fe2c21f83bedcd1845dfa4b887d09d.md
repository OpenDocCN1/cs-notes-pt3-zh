# 一、输出文字

+   三种方法实现以指定字体和颜色在指定位置输出文字：
+   
+   1. `drawString(String str, int x, int y)`  
+      使用此图形上下文的当前字体和颜色绘制由指定 string 给定的文本。
+   
+   2. `drawChars(char[] data, int offset, int length, int x, int y)`  
+      使用此图形上下文的当前字体和颜色绘制由指定字符数组给定的文本。
+   
+   3. `drawBytes(byte[] data, int offset, int length, int x, int y)`  
+      使用此图形上下文的当前字体和颜色绘制由指定 byte 数组给定的文本。