# # 字符串输入函数

+   - `istream& istream::get (char* &pArray, streamsize n, char delim = '\n');`

作用：读取一段文本，并将输入的字符串以及一个空字符一起存储，**将指定的终止符留在流中。**  
如读取失败(遇EOF) 则流istream对象设置错误标志，不能继续进行输入操作。

```
```cpp
char str[20];
cin >> str;
cin.get (str, 20);
```
```