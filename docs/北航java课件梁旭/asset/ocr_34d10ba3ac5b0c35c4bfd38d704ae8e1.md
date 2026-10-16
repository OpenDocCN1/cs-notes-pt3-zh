# 1. Thread类

+   - 继承Thread类并重载run方法。
+   - Thread类：是专门用来创建线程和对线程进行操作的类。代表Java程序的单个线程。Thread中定义了许多方法对线程进行操作。在java.lang包。

+   - （1）构造方法：

```
public Thread(ThreadGroup group, Runnable target, String name)
```

创建一个新的线程对象。

+   - group指明了线程所属的线程组；
+   - target是线程体run()方法所在的对象；
+   - name是线程的名称。
+   - 以上3个参数可任意组合，或者都不写，实现构造方法的多个重载。