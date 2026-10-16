# 中介者模式

# 模式分析

+   典型的具体同事类代码：

```
class ConcreteColleague extends Colleague {
    public ConcreteColleague(Mediator mediator) {
        super(mediator);
    }
    //实现自身方法
    public void method1() {
        .....
    }
    //定义依赖方法，与中介者进行通信
    public void method2() {
        mediator.operation();
    }
}
```

在具体同事类中实现了在抽象同事类中声明的方法，其中method1()方法是同事类的自身方法(Self-Method)，用于处理自己的行为，而method2()方法是依赖方法(Depend-Method)，用于调用在中介者中定义的方法，依赖中介者来完成相应的行为，例如调用另一个同事类的相关方法。