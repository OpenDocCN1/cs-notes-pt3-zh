
## 取得和设置线程名称

- 在Thread类中，可以通过getName()方法取得线程的名称，通过setName()方法设置线程的名称。
- 线程的名称一般在启动线程前设置，但也允许为已经运行的线程设置名称。允许两个Thread对象有相同的名字，但为了清晰，应该尽量避免这种情况的发生。
- 另外，如果程序并没有为线程指定名称，则系统会自动的为线程分配一个名称。

## 设置和取得线程的名字

```
class MyThread implements Runnable{        // 实现Runnable接口
    public void run() {                    // 覆盖接口中的run()方法
        for(int i=0;i<3;i++){               // 循环输出3次
            System.out.println(Thread.currentThread().getName()
                + "运行， i = " + i) ;
            // 取得当前线程的名字
        }
    }
};
public class ThreadNameDemo {
    public static void main(String args[]) {
        MyThread my = new MyThread() ;          // 定义Runnable子类对象
        new Thread(my).start() ;                // 系统自动设置线程名称
        new Thread(my,"线程-A").start() ;       // 手工设置线程名称
        new Thread(my,"线程-B").start() ;       // 手工设置线程名称
        new Thread(my).start() ;                // 系统自动设置线程名称
        new Thread(my).start() ;                // 系统自动设置线程名称
    }
};
```

## 程序说明

- 从运行结果中发现没有设置线程名称的其余三个线程对象的名字都是很有规律的：Thread-0、Thread-1、Thread-2，从之前讲解的static关键字可以知道，在Thread类中必然存在一个static类型的属性，用于为线程自动命名。

## 观察程序的输出

```
class MyThread implements Runnable{        // 实现Runnable接口
    public void run() {                    // 覆盖接口中的run()方法
        for(int i=0;i<3;i++){               // 循环输出3次
            System.out.println(Thread.currentThread().getName()
                + "运行， i = " + i) ;
            // 取得当前线程的名字
        }
    }
};
public class CurrentThreadDemo {
    public static void main(String args[]) {
        MyThread my = new MyThread() ;        // 定义Runnable子类对象
        new Thread(my,"线程").start() ;       // 启动线程
        my.run() ;                            // 直接调用run方法
    }
};
```

## 判断线程是否启动

- 通过Thread类之中的start()方法通知CPU这个线程已经准备好启动，之后就等待分配CPU资源，运行此线程了。那么如何判断一个线程是否已经启动了呢？在Java中可以使用isAlive()方法来测试线程是否已经启动而且仍然在运行。

```
class MyThread implements Runnable { // 实现Runnable接口
    public void run() { // 覆盖run()方法
        for (int i = 0; i < 3; i++) { // 循环输出3次
            System.out.println(Thread.currentThread().getName()
                + "运行 --> " + i); // 取得当前线程名称
        }
    }
};
public class ThreadAliveDemo {
    public static void main(String args[]) {
        MyThread mt = new MyThread(); // 实例化对象
        Thread t = new Thread(mt, "线程"); // 实例化Thread对象
        System.out.println("线程开始执行之前 --> " + t.isAlive());// 判断是否启动
        t.start(); // 启动线程
        System.out.println("线程开始执行之后 --> " + t.isAlive());// 判断是否启动
        for (int i = 0; i < 3; i++) { // 循环输出3次
            System.out.println(" main 运行 --> " + i); // 输出
        }
        System.out.println("代码执行之后 --> " + t.isAlive());// 后面的输出结果不确定
    }
};
```

## 线程的强制运行

- 在线程操作中，可以使用join()方法让一个线程强制运行，线程强制运行期间，其他线程无法运行，必须等待此线程完成之后才可以继续执行。

```
class MyThread implements Runnable { // 实现Runnable接口
    public void run() { // 覆盖run()方法
        for (int i = 0; i < 50; i++) { // 循环50次
            System.out.println(Thread.currentThread().getName()
                + "运行 --> " + i); // 输出线程名称
        }
    }
};
public class ThreadJoinDemo {
    public static void main(String args[]) {
        MyThread mt = new MyThread(); // 实例化对象
        Thread t = new Thread(mt, "线程"); // 实例化Thread对象
        t.start(); // 线程启动
        for (int i = 0; i < 50; i++) { // 循环50次
            if (i > 10) { // 判断变量内容
                try {
                    t.join(); // 线程t进行强制运行
                } catch (Exception e) {} // 需要进行异常处理
            }
            System.out.println("Main 线程运行 --> " + i);
        }
    }
};
```

## 线程的休眠

- 在程序中允许一个线程进行暂时的休眠，直接使用Thread.sleep()方法即可。

```
class MyThread implements Runnable {        // 实现Runnable接口
    public void run() {                     // 覆盖run()方法
        for (int i = 0; i < 5; i++) {        // 循环5次
            try {
                Thread.sleep(500);           // 线程休眠
            } catch (Exception e) {}         // 需要异常处理
            System.out.println(Thread.currentThread().getName()
                + "运行， i = " + i);        // 输出线程名称
        }
    }
};
public class ThreadSleepDemo {
    public static void main(String args[]) {
        MyThread mt = new MyThread();        // 实例化对象
        new Thread(mt, "线程").start();      // 启动线程
    }
};
```
