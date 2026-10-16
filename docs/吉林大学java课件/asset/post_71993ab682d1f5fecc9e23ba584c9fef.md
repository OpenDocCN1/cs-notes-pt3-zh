
## notify()和notifyAll()

对于唤醒的操作有两个：notify()、notifyAll()。一般来说，所有等待的线程会按照顺序进行排列，如果现在使用了notify()方法的话，则会唤醒第一个等待的线程执行，而如果使用了notifyAll()方法，则会唤醒所有的等待线程，那个线程的优先级高，那个线程就有可能先执行。

![](img/b706331eacf49a62651c2c9b2de81ca5_488_0.png)

## 问题解决2 —— 加入等待与唤醒

如果要想让生产者不重复生产，消费者不重复取走，则可以增加一个标志位，假设标志位为boolean型变量，如果标志位的内容为true，则表示可以生产，但是不能取走，如果此时线程执行到了消费者线程则应该等待，如果标志位的内容为false，则表示可以取走，但是不能生产，如果生产者线程运行，则应该等待。

![](img/b706331eacf49a62651c2c9b2de81ca5_489_0.png)

![](img/b706331eacf49a62651c2c9b2de81ca5_489_1.png)

## 修改Info类

```
class Info {
    // 定义信息类
    private String name = "李兴华";
    // 信息名称，指定默认值
    private String content = "JAVA讲师";
    // 信息内容，指定默认值
    private boolean flag = false ;
    // 设置标志位
    public synchronized void set(String name, String content) {
    // 设置信息名称及内容
        if(!flag){
        // 标志位为false, 不可以生产
            super.wait() ;
        // 等待消费者取走, 处理异常
        }
        this.setName(name);
        // 设置信息名称
        Thread.sleep(300);
        // 加入延迟, 处理异常
        this.setContent(content) ;
        // 设置信息内容
        flag = false ;
        // 修改标志位, 表示可以取走
        super.notify() ;
        // 唤醒等待线程
    }
    public synchronized void get() {
    // 取得信息内容
        if(flag){
        // 标志位为true, 不可以取走
            super.wait() ;
        // 等待生产者生产, 处理异常
        }
        Thread.sleep(300);
        // 加入延迟, 处理异常
        System.out.println(this.getName() + " --> " + this.getContent()); // 输出信息
        flag = true ;
        // 修改标志位为true, 表示可以生产
        super.notify() ;
        // 唤醒等待线程
    }
    // setter()及getter()方法
}
```

## 下一章内容

## 线程生命周期

![](img/b706331eacf49a62651c2c9b2de81ca5_491_0.png)

## 多线程
—— 线程生命周期

## 本章目标

- □ 了解线程的生命周期
- □ 了解线程的停止操作

## 线程的生命周期

![](img/b706331eacf49a62651c2c9b2de81ca5_494_0.png)

## 停止线程运行

- 既然以上的三个方法不推荐使用，那么该如何停止一个线程的执行呢？在多线程的开发中可以通过设置标志位的方式停止一个线程的运行。

## 停止线程运行

```
class MyThread implements Runnable {
    private boolean flag = true;                         // 定义标志位属性
    public void run() {                                  // 覆盖run()方法
        int i = 0;
        while (this.flag) {                               // 循环输出
            System.out.println(Thread.currentThread().getName() + "运行, i = " + (i++));
            // 输出当前线程名称
        }
    }
    public void stop() {                                 // 编写停止方法
        this.flag = false;                               // 修改标志位
    }
}
public class StopDemo {
    public static void main(String[] args) {
        MyThread my = new MyThread();                    // 实例化Runnable接口对象
        Thread t = new Thread(my, "线程");               // 建立线程对象
        t.start();
        try(Thread.sleep(10);
        }
        catch(Exception e){}
        // 启动线程
        my.stop();                                       // 线程停止，修改标志位
    }
}
```

## 泛型
—— 泛型入门

## 本章目标

- - 掌握泛型的产生意义
- - 掌握泛型的基本使用
- - 了解泛型的警告信息及泛型的擦除

## 题目分析

一看到这样的要求，读者首先就要考虑到，必须建立好一个表示坐标点的类 —— Point，此类中有两个属性分别用来表示x坐标和y坐标，但是x和y中所保存的数据类型会有三种（int、float、String），而要想使用一个类类型可以同时接收这样的三种类型数据，则现在只能使用Object，因为Object类可以接收任何类型的数据，都会自动发生向上转型操作，这样三种数据类型将按以下的方式进行转换：

- 数字（int） → 自动装箱成Integer → 向上转型使用Object接收
- 小数（float） → 自动装箱成Float → 向上转型使用Object接收
- 字符串（String） → 向上转型使用Object接收

![](img/b706331eacf49a62651c2c9b2de81ca5_501_0.png)

## 设计Point类

```
class Point {
    private Object x;                // 表示x坐标
    private Object y;                // 表示y坐标
    public void setX(Object x) {
        this.x = x;
    }
    public void setY(Object y) {
        this.y = y;
    }
    public Object getX() {
        return this.x;
    }
    public Object getY() {
        return this.y;
    }
};
```

## 代码的问题

```
public class GenericsDemo04 {
    public static void main(String[] args) {
        Point p = new Point();
        p.setX(10);    // 利用自动装箱操作: int --> Integer --> Object
        p.setY("北纬210度");    // String --> Object
        int x = (Integer)p.getX();    // 取出数据
        int y = (Integer)p.getY();    // 取出数据 →此处出现了类转换错误
        System.out.println("整数表示, x坐标为: " + x);
        System.out.println("整数表示, y坐标为: " + y);
    }
}
```
