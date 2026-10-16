# 使用接口定义常量值

因为接口内的属性都是static和final的，所以我们可以很方便的利用这一点来创建一些常量。

```
public interface Constants {
    String ROOT = "/root";
    int MAX_COUNT = 200;
    int MIN_COUNT = 100;
}
```

在使用时可以直接用Constants.ROOT这样的形式来引用其中的常量。