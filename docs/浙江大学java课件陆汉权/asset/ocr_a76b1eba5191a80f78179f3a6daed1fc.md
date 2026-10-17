# In Java

+   - 关键字 extends
+     - 指示所建立的新的类 ExStudent 派生于已经存在的类 Student —— 继承
+     - 已经存在的类 Student 称为
+       - 超类 superclass，或者
+       - 基类 base class，或者
+       - 父类 parent class
+     - 新的类 ExStudent 称为
+       - 派生类 derived class，或者
+       - 子类 subclass，或者
+       - 孩子类 child class
+   - 有趣的：
+     - 子类比父类具有更多的功能

```
class Student {
    ......
}
class ExStudent extends Student {
    // 加上有关获类的成员变量和方法
}
```