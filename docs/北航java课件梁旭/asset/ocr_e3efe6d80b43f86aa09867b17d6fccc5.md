# 2.6 简单的输出与输入

+   - 二、简单的输入举例
+   - 1、字符数据输入

+   - System.in.read();//从键盘读取单个字符;
+   - Read()方法得到的是字符的字节表示形式，需要使用强制转换转化为字符形式，如 char c=(char)System.in.read();
+   - 因为可能产生IO异常，此方法要在try......catch中使用。

+   - 例程：

```
try {
    char c=(char)System.in.read();
}
catch (IOException ex) {System.out.println(ex); }
```