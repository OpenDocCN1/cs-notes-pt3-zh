
## 接口

+   □ 接口是java中最重要的概念，接口可以理解为一种特殊的类，里面全部是由全局常量和公共的抽象方法所组成。

![](img/b706331eacf49a62651c2c9b2de81ca5_274_0.png)

不需要知道里面的几个元件

![](img/b706331eacf49a62651c2c9b2de81ca5_274_1.png)

不需要知道内部几个元件有怎样的具体实现

![](img/b706331eacf49a62651c2c9b2de81ca5_274_2.png)

## 接口的定义格式

```
interface 接口名称{
    全局常量；
    抽象方法；
}

注：接口中没有构造方法,不能被直接实例化
public interface A
{
    public A(){...}; //错,接口中不能包含构造方法
    void method();
}
```

## 接口的定义

+   完整格式：

```
interface A{
    public static final String AUTHOR = "李兴华" ;        // 定义全局常量
    public abstract void print() ;                         // 定义抽象方法
    public abstract String getInfo() ;                     // 定义抽象方法
}
```

+   简化格式：

```
interface A{
    String AUTHOR = "李兴华" ;        // 等价于: public static final String
    AUTHOR = "李兴华" ;
    void print() ;                      // 等价于: public abstract void print() ;
    String getInfo() ;                  // 等价于: public abstract String
    getInfo() ;
}
```

## 使用接口定义常量值

因为接口内的属性都是static和final的，所以我们可以很方便的利用这一点来创建一些常量。

```
public interface Constants {
    String ROOT = "/root";
    int MAX_COUNT = 200;
    int MIN_COUNT = 100;
}
```

在使用时可以直接用Constants.ROOT这样的形式来引用其中的常量。

## 接口图形表示

+   接口的图形可以按照类图的形成表示，也可以使用的一个“○”表示

![](img/b706331eacf49a62651c2c9b2de81ca5_278_0.png)

![](img/b706331eacf49a62651c2c9b2de81ca5_278_1.png)

## 实现接口

+   - 与抽象类一样，接口要使用也必须通过子类，子类通过implements关键字实现接口。
+   - 实现格式：
+     - `class 子类 implements 接口A,接口B,...{ }`
+   - 当类实现了某个Java接口时,它必须实现接口中的所有抽象方法,否则这个类必须声明为抽象的
+   - 不允许创建接口的实例(实例化),但允许定义接口类型的引用变量,该引用变量引用实现了这个接口的类的实例
+     - `public class B implements A{}`
+     - `A a = new B(); //引用变量a被定义为A接口类型,引用了B实例`
+     - `A a = new A(); //错误,接口不允许实例化`

## 实现接口

```
```java
interface A{
	public String AUTHOR = "李兴华" ; // 定义接口A
	public void print() ; // 定义全局常量
	public String getInfo() ; // 定义抽象方法
}

interface B{
	public void say() ; // 定义接口B
}

class X implements A,B{
	public void say() {
		System.out.println("Hello World!!!");
	}
	public String getInfo() {
		return "HELLO";
	}
	public void print() {
		System.out.println("作者: " + AUTHOR);
	}
}
```
```

## 接口的实现

以上的程序中，一个子类同时实现了两个接口，这样在子类中就必须同时覆盖完两个接口中的全部抽象方法

![](img/b706331eacf49a62651c2c9b2de81ca5_281_0.png)

## 继承抽象类实现接口

+   □ 一个子类可以同时继承抽象类和实现接口。
+   □ 格式如下：
+     ✧ class 子类 extends 抽象类 implements 接口A,接口B,...{}

## 子类同时继承抽象类和实现接口

```
interface A{ // 定义接口A
    public String AUTHOR = "李兴华"; // 定义全局常量
    public void print(); // 定义抽象方法
    public String getInfo(); // 定义抽象方法
}
abstract class B{ // 定义抽象类 B
    public abstract void say();
}
class X extends B implements A{ // 子类同时实现接口
    public void say() { // 覆盖抽象类B中的抽象方法
        System.out.println("Hello World!!!");
    }
    public String getInfo() { // 覆盖接口A中的抽象方法
        return "HELLO";
    }
    public void print() { // 覆盖接口A中的抽象方法
        System.out.println("作者: " + AUTHOR);
    }
}
```

## 接口和抽象类的使用限制

在java中允许一个抽象类实现多个接口的

```
interface A{ // 定义接口A
    public String AUTHOR = "李兴华"; // 定义全局常量
    public void print(); // 定义抽象方法
    public String getInfo(); // 定义抽象方法
}
abstract class B implements A{ // 定义抽象类，实现接口
    public abstract void say(); // 此时抽象类中存在三个抽象方法
}
class X extends B{ // 子类继承抽象类
    public void say() { // 覆盖抽象类B中的抽象方法
        System.out.println("Hello World!!!");
    }
    public String getInfo() { // 覆盖抽象类B中的抽象方法
        return "HELLO";
    }
    public void print() { // 覆盖抽象类B中的抽象方法
        System.out.println("作者: " + AUTHOR);
    }
}
```

## 接口的继承

+   一个接口不能继承一个抽象类，但是却可以通过extends关键字同时继承多个接口，实现接口的多继承。
+   格式：
+     interface 子接口 extends 父接口A,父接口B,...{}

## 接口的多继承

```
interface A{ // 定义接口A
    public String AUTHOR = "李兴华"; // 定义全局常量
    public void printA(); // 定义抽象方法
}
interface B{ // 定义接口B
    public void printB(); // 定义抽象方法
}
interface C extends A,B{ // 定义接口C，同时继承接口A、B
    public void printC(); // 定义抽象方法
}
class X implements C{ // 子类实现接口C
    public void printA() { // 覆盖接口A中的printA()方法
        System.out.println("A. Hello World");
    }
    public void printB() { // 覆盖接口B中的printB()方法
        System.out.println("B. Hello MLDN");
    }
    public void printC() { // 覆盖接口C中的printC()方法
        System.out.println("C. Hello LXH");
    }
}
```
