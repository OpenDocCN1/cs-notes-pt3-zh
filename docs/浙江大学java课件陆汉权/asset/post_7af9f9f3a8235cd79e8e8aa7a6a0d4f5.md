
## 13.1.2 Applet程序的运行过程

- 当浏览器装载有带Applet程序的网页时：
  - 首先为Applet及其全局变量分配存储空间。
  - 执行Applet的init()方法。
  - 执行Applet的start()方法。
  - 执行Applet的paint()方法。
- 当离开Applet网页，又重新激活时：
  - 执行Applet的start()方法。
  - 执行Applet的paint()方法。
- 当用户真正离开浏览器时：
  - 执行Applet的stop()方法。
  - 执行Applet的destroy()方法。

## 13.1.3 Applet程序的建立和运行

建立方法：
1. 用文本编辑器编辑源程序：文件名.java
2. 用javac.exe编译源程序，生成字节码文件：文件名.class
3. 将字节码文件嵌入到HTML文件中。
4. 浏览加载HTML文件时，执行Applet程序。

```html
<HTML>
<APPLET CODE="applet类名.class" WIDTH=窗口宽度 HEIGHT=窗口高度></APPLET>
</HTML>
```

applet类名.class：即为字节码文件

窗口宽和高度是指Applet程序运行时的窗口初始尺寸。

运行Applet程序的几种方式：
1. 利用浏览器运行Applet程序。
2. 利用appletviewer运行Applet程序。appletviewer html文件名.htm
3. 利用JCreator或Eclipse建立和运行Applet程序。

## Applet程序举例：显示文字：Hello Applet!

```java
import java.awt.Graphics;
import javax.swing.JApplet;
public class T1 extends JApplet{
public void paint(Graphics g){
g.drawString("Hello Applet!",50,60);
}
}
```

HTML文件(在T1.class同一文件夹中):

```html
<HTML>
<APPLET CODE="T1.class" WIDTH=250
HEIGHT=100></APPLET>
</HTML>
```

![](img/80da1d99a94a92757465da523b64f0ce_500_0.png)

使用浏览器执行(HTML)

![](img/80da1d99a94a92757465da523b64f0ce_500_1.png)

使用Eclipse执行

## Applet程序举例：绘制图形

```java
import java.awt.Graphics;
import javax.swing.JApplet;
public class E13_2 extends JApplet{
    public void paint(Graphics g){
        g.drawLine(40,30,200,30);  //画横线，两点：(40,30)和(200,30)
        g.drawRect(40,50,160,100);  //画矩形，(40,50)为左上角，宽和高分别为160和100
        g.drawOval(40,50,160,100);  //画椭圆。(40,50)为左上角，宽160高100的矩形为切椭圆
        g.drawLine(40,170,200,170);
        g.drawString("Drawing!",100,105);  //(100,100)处输出字符串
    }
}
```

HTML文件：

```html
<HTML>
<APPLET CODE="E13_2.class"
             WIDTH=250 HEIGHT=200>
</APPLET>
</HTML>
```

![](img/80da1d99a94a92757465da523b64f0ce_501_0.png)

Applet举例：覆盖init()方法的Applet程序。利用init()方法输入一个整数，利用paint()方法计算并输出阶乘。

```java
import java.awt.Graphics;
import javax.swing.*;   // JOptionPane和JApplet
public class T1 extends JApplet{
    int n;
    long s=1;
    public void init(){
        String nStr=JOptionPane.showInputDialog("请输入一个整数：");
        n=Integer.parseInt(nStr);
    }
    public void paint(Graphics g){
        for(int i=1;i<=n;i++)s*=i;
        g.drawString (n+"!="+s,10,10);
    }
}
```

```html
<HTML>
<Applet code=T1.class width=300 height=100></Applet>
</Html>
```

![](img/80da1d99a94a92757465da523b64f0ce_502_0.png)

## 第十四章

## 多线程

- 许多程序都包含了一些独立的代码段，如果让它们在执行时间上重叠，可以提高执行效率。
- **线程是为了实现重叠执行而引入的一个概念。**
- **线程是可以独立、并发执行的程序单元。**
- 多线程是指程序中存在多个执行体，按自己的执行步骤并发工作，独立完成各自功能，互不干扰。

## 14.1 Java的多线程机制

- 多线程机制是Java的重要特征。
- 每个Java程序都有一个主线程
  ——main()方法对应的线程。
- 实现多线程，必须在主线程中创建新线程。
- Java线程用Thread类及子类的对象来表示。
- 每个线程经历五种状态。从新生到死亡的过程为生命周期。

## 线程的生命周期

1. 新生状态：用new运算符和Thread类或子类建立一个线程。
   - 新生状态的线程有自己的内存空间。
   - 通过调用start()方法进入就绪状态。
2. 就绪状态：已具备运行条件，等待系统为它分配CPU。
   - 一旦获得CPU，就进入运行状态，并自动调用run()方法。
3. 运行状态：执行run()方法中的代码，直到调用其他方法而终止。或等待某资源而阻塞，或完成任务而死亡。
4. 阻塞状态：运行状态下，若执行了sleep()方法、或等待I/O设备等，让出CPU而暂停运行，即进入了阻塞状态。
   - 阻塞状态的线程不能进入就绪队列。
   - 只有当阻塞原因消除后，才转入就绪状态。
5. 死亡状态：正常运行的线程完成了它全部工作。或强制终止，如执行了stop()或destroy()方法。

## 14.1.2 多线程的实现方法

- 有两种方法：
  1. 通过创建Thread类的子类来实现。
  2. 通过实现Runnable接口的类来实现。

两者无本质区别，只是由于Java不允许多重继承，所以当一个类既要继承一个非Thread类，又要实现多线程时，可以使用Runnable接口的方式。

## 举例:通过Thread类实现多线程

1. 先设计Thread类的子类（即继承Thread类）
2. 设计线程的run()方法
3. 建立该类的对象
4. 使用start()方法启动线程，将执行权交给run()方法。

[例14-1]通过继承Thread类实现多线程。启动两个线程执行。它们分别相隔m毫秒输出一个字母A或B（m分别为50和100）。共输出20个A和20个B。

```java
public class T1 extends Thread{ //继承Thread
String s;
int m,count=0;
T1(String ss,int mm){ s=ss; m=mm; }
public void run(){
try{
while(true){
System.out.print(s);
sleep(m); //sleep m毫秒
count++;
if(count>=20)break;
}
System.out.println("finished"+s+"!");
}
catch(InterruptedException e){
return ;
}
}
```

```java
public static void main(...){
T1 threadA=new T1("A ",50);
T1 threadB=new T1("B ",100);
threadA.start(); //启动线程
threadB.start(); //启动线程
}
}
```

运行后的输出：
A B A A B A A B B A A B A A B A A B B
A A B A A B A A B A A B A finishedA !
B B B B B B B B B B finishedB !
