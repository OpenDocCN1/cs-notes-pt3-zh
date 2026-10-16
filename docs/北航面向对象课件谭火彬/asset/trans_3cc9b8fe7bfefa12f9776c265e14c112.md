
## 根据类图试写Button代码

```java
public class Button {
    private Dialer myDialer;
    public Button(Dialer dialer) {
        myDialer = dialer;
    }
    public void buttonPressed(String token) throws NumberFormatException {
        int digit = Integer.parseInt(token);
        myDialer.digit(digit);
    }
}
```

Button与Dialer之间出现耦合，从而破坏了Button的可复用性。

我们考虑增加一个间接层来解决？

## 添加一个间接层？

- 添加一个怎样的类？
- 两个关系是怎样的？

![](img/32b9da3a6e0f048e7dd2e9664c939f9e_519_0.png)

## 改进设计—将行为赋予接口

![](img/32b9da3a6e0f048e7dd2e9664c939f9e_520_0.png)

面向对象设计对付类耦合的基本对策：将两个类之间的关联转变为一个类与一个接口之间的关联，或者两个接口之间的关联。

## 新的问题？

```java
interface ButtonListener {
    public void buttonPressed(int token);
}

public class Dialer implements ButtonListener {
    public void buttonPressed(int token) { ... }
}
```

新问题：Dialer需要实现ButtonListener接口，即要实现buttonPressed()方法？并要求Dialer能够接受int型的数值并组装为电话号码进行拨号？如果Dialer是已经做好的配件，只接受一个字符串表示的电话号码，又该怎么办？这种设计限制了Dialer的可复用性。

## 再增加一个间接层

![](img/32b9da3a6e0f048e7dd2e9664c939f9e_522_0.png)

## GoF：适配器（Adapter）模式

目的：将一个类的接口转换成客户希望的另外一个接口；适配器模式使得原本由于接口不兼容而不能一起工作的那些类可以一起工作。

**结构：**

**适用性：**

- 你想使用一个已经存在的类，而它的接口不符合你的需求；
- 你想创建一个可以复用的类，该类能够与不相关的类，即一些没有预期接口的类协同工作；
- 你想使用一些已经存在的子类，但是不可能对每一个都进行子类化以匹配它们的接口。对象适配器可以适配它的父类接口。

![](img/32b9da3a6e0f048e7dd2e9664c939f9e_523_0.png)

## 代码实现

```java
interface ButtonListener {
    void buttonPressed(int digit);
}

public class Dialer {
    public void dial(String pno) { radio.connect(pno); }
}

public class ButtonDialerAdapter implements ButtonListener {
    StringBuffer myPho = new StringBuffer();
    Dialer myDialer;
    ...
    public void buttonPressed(int digit) {
        if (digit == DIAL_SIGNAL)
            myDialer.dial(myPho.toString());
        else
            myPho.append(digit);
    }
}
```

## 引发潜在问题

![](img/32b9da3a6e0f048e7dd2e9664c939f9e_525_0.png)

既然Dialer只在拨号时反应，那么按下数字键时，如何让Speaker发声？

## 如法炮制

![](img/32b9da3a6e0f048e7dd2e9664c939f9e_526_0.png)

现在的关键问题是，Button必须可以在被按下的时候，通知数量未知的监听者，或者说“观察者（observer）”。

## GoF：观察者（Observer）模式

- 目的：定义对象间的一种一对多的依赖关系，当一个对象的状态发生改变时，所有依赖于它的对象都得到通知并被自动更新。
- 结构：
- 适用性：
  - 当一个对象必须通知其它对象，而它又不能假定其它对象是谁。换言之，你不希望这些对象紧密耦合。

![](img/32b9da3a6e0f048e7dd2e9664c939f9e_527_0.png)

## 实现观察者模式

```java
public class Button {
    private int myDigit = INVALID_DIGIT;
    private LinkedList observers = new LinkedList();

    boolean addObserver(ButtonListener bl) {
        return observers.add(bl);
    }

    void pressed() {
        ListIterator li = observers.listIterator();
        while (li.hasNext()) {
            ButtonListener bl = (ButtonListener) li.next();
            bl.buttonPressed(myDigit);
        }
    }
}
```

## 换个思路

![](img/32b9da3a6e0f048e7dd2e9664c939f9e_529_0.png)

对于Button本身来说，它只需要知道自己是否被按下，如果被按下，则触发一个操作，而具体触发什么操作应该由相应的实施该操作的类来实现。

## GoF：命令（Command）模式

目的：将一个请求封装为一个对象，从而使你可用不同的请求对客户进行参数化；对请求排队或记录请求日志，以及支持可撤消的操作。

**结构：**

**适用性：**

- 抽象出待执行的动作以参数化对象。
- 在不同的时刻指定、排列和执行请求。
- 支持撤消操作。
- 支持修改日志，这样当系统崩溃时，这些修改可以被重做一遍。
- 用构建在原语操作上的高层操作构造一个系统。

![](img/32b9da3a6e0f048e7dd2e9664c939f9e_530_0.png)

## 运用命令模式的Button

```java
interface Command { public void do(int signal); }

public class Button {
    Command cmd = null;
    int digit = 0;
    public Button(Command cmd) { this.cmd = cmd; }
    public Command setCommand(Command cmd) {
        Command old = this.cmd;
        this.cmd = cmd;
        return old;
    }
    public final void pressed() {
        cmd.do(digit);
    }
}
```

## 更多的模式....

- 空对象（Null Object）
- 抽象服务器（Abstract Server）
- 主动对象（Active Object）
- ......

## 空对象（Null Object）模式

```java
Employee e = DB.getEmployee("Bob");
if (e != null && e.isTimeToPay(today))
    e.pay();
```

![](img/32b9da3a6e0f048e7dd2e9664c939f9e_533_0.png)

```java
Employee e = DB.getEmployee("Bob");
if (e.isTimeToPay(today))
    e.pay();
```

## 内容安排

- ☑ 模式基础
- ☑ 设计模式
- ☑ GoF设计模式及应用
- ☑ GRASP职责分配模式
- ☑ 模式与编程语言
- ☑ 模式与重构

## 责任

☑ 责任（Responsibility）：一个类或类型的契约或者义务；它与对象在行为上的义务密切相关；可分为两类职责：

- **“知道”型职责**
  - 知道自己的私有的、封装了的数据
  - 知道与自己相关联的对象信息
  - 知道自己派生出来或者计算出来的事物
- **“做”型职责**
  - 自己完成某件任务
  - 发起其他对象执行动作
  - 控制和协调其他对象内的活动

