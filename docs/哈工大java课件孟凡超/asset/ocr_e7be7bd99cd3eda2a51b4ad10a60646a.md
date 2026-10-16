# 3.1 表达式

✓ final关键字与static关键字同时使用

例如：

```
final long CURRENT_TIME=system.currentMillis();
```

```
static final long CURRENT_TIME=system.currentMillis();
```

+   • 不使用static修饰： 如果建立常量时直接赋一个固定值，那么这个常量的值是固定不变的，即多个对象中的值也是相同的。如果建立常量时是采用函数或对象，那么每次建立对象时给其常量的初始化值就有可能不同。所以，只使用final的Java常量定义并不是恒定的。

+   • 使用static修饰： 在创建对象之前就会为这个变量在内存中创建一个存储空间，以后创建对象如果需要用到这个静态常量，那么就共享这一个变量的存储空间。