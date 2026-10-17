# 实现Callback接口的例子程序：

```
class Client implements Callback {
// Implement Callback's interface
public void callback(int p) { // 必须声明成public
System.out.println("callback called with " + p);
}
}
```

# 定义它自己的附加的成员：

```
class Client implements Callback {
// Implement Callback's interface
public void callback(int p) {
System.out.println("callback called with " + p);
}
void nonIfaceMeth() { // 增加了nonIfaceMeth()方法
System.out.println("Classes that implement interfaces " +
"may also define other members, too.");
}
}
```