# 匿名对象

+   只使用一次的对象，称为匿名对象。
+   匿名对象只在堆内存中开辟空间，而不存在栈内存的引用。

```
public class NonameDemo01 {
    public static void main(String args[]) {
        new Person("张三", 30).tell();    // 匿名对象
    }
}
```