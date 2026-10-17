

程序运行结果如下：

null　 null　 0

张三　 西安市兴庆路1号　 75

## 使用无参数的构造方法

```java
class Time {                    // 教材例6-5，类Time
    private int hour;           // 0-23
    private int minute;         // 0-59
    private int second;         // 0-59

    public Time() {
        setTime(0,0,0);
    }

    public void setTime(int hh, int mm, int ss) {
        hour = ((hh >= 0 && hh <24) ? hh : 0);     // 使hour在0-23之间
        minute = ((mm >= 0 && mm < 60) ? mm : 0);
        second = ((ss >= 0 && ss < 60) ? ss : 0);
    }

    public String toString() {
        return (hour + ":" + (minute < 10 ? "0" : "") + minute +
            ":" + 
            (second < 10 ? "0" : "") + second );
    }
}
// 类 Time结束
```

```java
public class MyTime { // 程序中的第二个类 MyTime
public static void main(String args[]) {
    Time time=new Time();
    time.setTime(11,22,33);
    System.out.println(" set time =" + time.toString());
}
}
```

## 编程与运行

- 在Java中，每个类是一个独立的程序段，是一个Java文件
- 本例中，有两个类，因此有两个Java文件，分别建立
- 这两个程序被打“包”（Packet），成为一个整体程序
- 能够被运行的程序是内有main()方法的类

运行结果如下：
set time =11:22:33

## 使用多个构造方法

```java
class Time1
{
    private int hour;          //0-23
    private int minute;        //0-59
    private int second;        //0-59
    public Time1()
    { setTime (0,0,0); }
    public Time1(int hh)
    { setTime (hh,0,0); }
    public Time1 (int hh, int mm)
    { setTime (hh,mm,0); }
    public Time1(int hh, int mm, int ss)
    { setTime (hh,mm,ss); }

    public void setTime(int hh, int mm, int ss)
    {
        hour = ((hh >= 0 && hh < 24) ? hh : 0);
        minute = ((mm >= 0 && mm < 60) ? mm : 0);
        second = ((ss >= 0 && ss < 60) ? ss : 0);
    }

    public String toString()
    {
        return (hour + ":" + (minute < 10 ? "0" : "") + minute + ":" +
                (second < 10 ? "0" : "") + second);
    }
}
```

```java
public class MyTime1
{
private static Time1 t0, t1, t2, t3;
public static void main(String args[])
{
t0=new Time1();
t1=new Time1(11);
t2=new Time1(22, 22);
t3=new Time1(33, 33, 33);
System.out.println(" t0= " + t0.toString());
System.out.println("t1= " + t1.toString());
System.out.println("t2= " + t2.toString());
System.out.println("t3= " + t3.toString());
} }
```

程序运行结果如下：
t0= 0:00:00
t1= 11:00:00
t2= 22:22:00
t3= 0:33:33

## 对象的销毁

- new运算符实例化对象
  - 过程：系统为对象分配所需的存储空间
  - 但内存空间有限，不能存放无限多的对象
  - 为此，Java提供了资源回收机制，自动销毁无用对象，回收其所占用的存储空间
- 如需主动释放对象，或在释放时执行特定操作，则在类中可以定义 finalize() 方法：

```java
public void finalize()
{
    方法体;
}
```

## About Class

- 类是Java程序的构成，每一个类是一个整体
- 类中包括：
  - 成员变量 → 数据，如何被访问，被谁访问？
  - 成员方法 → 对数据(成员变量)进行操作
- 特点：
  - 可以定义不同的访问方法 → 成员变量
- 这个特点就是封装！

## 6.2.1 访问权限

Java的成员访问权限通过关键字 private，public，protected，缺省(不用关键字)实现

- public （公有）
  成员变量和成员方法可以Java在所有类中访问

- protected （保护）
  成员变量和成员方法可在声明他们的类中访问
  可以在在该类的子类中访问
  也可以在与该类位于同一包的类中访问——不能被其它包的非子类中访问

## 访问控制权限小结

| 访问控制 | 本类 | 同一包中的类 | 其他包中子类 | 其他包中的类 |
|---|---|---|---|---|
| public | √ | √ | √ | √ |
| private | √ | × | × | × |
| protected | √ | √ | √ | × |
| 缺省 | √ | √ | × | × |

## Java实例-权限修饰符的作用

```java
// 包里的第一个类
class Time {
    private int hour;    // 私有成员变量0-23
    private int minute;  // 0-59
    private int second;  // 0-59

    public Time () {     // 构造方法，初始化成员变量
        setTime(0,0,0);
    }
    public void setTime(int hh, int mm, int ss) { // 对成员变量操作
        hour = ((hh >= 0 && hh <24) ? hh : 0);
        minute = ((mm >= 0 && mm < 60) ? mm : 0);
        second = ((ss >=0 && ss < 60) ? ss : 0);
    }

    public String toString() {
       return (hour + ":" + (minute < 10 ? "0" : "") + minute + ":" +
              (second < 10 ? "0" : "") + second );
    }
}
```

```java
// 包里的第二个类
public class MyTime2 {
   public static void main(String args[]) {
      Time time = new Time();
      time.hour = 11;   // 给成员变量hour赋值： 非法访问， 因为
time类中的成员变量hour的属性是private
      System.out.println("time" + time.toString());
   }
}
```

