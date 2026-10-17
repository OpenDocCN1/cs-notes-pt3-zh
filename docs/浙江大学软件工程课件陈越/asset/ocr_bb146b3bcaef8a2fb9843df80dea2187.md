# 第12章　静态成员、友元

# 三、访问

类的静态成员必须通过类名来访问。

格式为：类名:: 静态成员名

```
如：File file1;

cout<<file1.fileCount;(×)

cout<<File:: fileCount;(√)
```