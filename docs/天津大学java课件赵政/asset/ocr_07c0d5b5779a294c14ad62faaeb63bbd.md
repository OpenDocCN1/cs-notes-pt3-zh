# 11.7.2 同步语句

+   - 在不知源代码时，不能在方法前加 synchronized。
+   - 需将对这个类定义的方法的调用放入一个 synchronized 块内。
+   - Synchronized 语句的普通形式：
+     ```java
+     synchronized(object) { //object是被同步对象的引用
+         // statements to be synchronized
+     }
+     ```
+   - 一个同步块确保对object成员方法的调用仅在当前线程成功进入object管程后发生。