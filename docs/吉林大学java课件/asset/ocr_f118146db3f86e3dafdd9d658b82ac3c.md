# 接口默认方法使用的几种情况

规则二：否则，调用定制最深的接口中的方法。

```
interface A {
    default void doSth() {
        System.out.println("inside A");
    }
}
interface B {}
interface C extends A {
    default void doSth() {
        System.out.println("inside C");
    }
}
class App implements C, B, A {
    public static void main(String[] args) {
        new App().doSth();
    }
}
```

运行结果： inside C