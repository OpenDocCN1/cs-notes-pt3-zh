

# AWT组件举例---在窗口中建立一个按钮

```java
import java.awt.*;
public class E11_3{
    public static void main(String []args){
        Frame fra=new Frame("按钮练习");
        Button but=new Button("click");
        fra.setLayout(null);   //没有这句，按钮会充满整个窗口
            //（加了这句，还要设置按钮大小，位置）
        fra.setSize(250,170);
        but.setSize(100,50);
        but.setLocation(75,60);
        fra.add(but);
        fra.setVisible(true);
    }
}
```

![](img/80da1d99a94a92757465da523b64f0ce_482_0.png)

## 11.2 布局管理

- 当窗口中组件较多时，用setSize和setLocation显得不方便。
- Java提供了多种布局管理器（Layout manager）：
- 用来对组件相对定位，会根据窗口大小，自动改变组件大小。
- 每一种布局管理器指定一种组件的相对布置和大小布局。
- Java提供了五种布局管理器类：
  - FlowLayout（提供按行布局组件的方式）
  - BorderLayout（把容器空间划分为东、南、西、北、中五个区域）
  - GridLayout（将容器划分为大小相等的若干行乘若干列的网格）
  - CardLayout
  - GridBagLayout
- 这些布局管理器类都是java.lang.Object的子类。

## 布局管理举例---使用FlowLayout布局。

```java
import java.awt.*;
public class E11_6{
public static void main(String []args){
Frame frm=new Frame("布局练习");
FlowLayout fl=new FlowLayout(FlowLayout.LEFT,5,10);//对齐，水平、垂直间距
frm.setBounds(0,0,300,200); //窗口初始位置和大小
frm.setLayout(fl); //采用FlowLayout布局
Button but1=new Button("Button1");
Button but2=new Button("Button2");
Button but3=new Button("Button3");
Button but4=new Button("Button4");
Button but5=new Button("Button5");
frm.add(but1);
frm.add(but2);
frm.add(but3);
frm.add(but4);
frm.add(but5);
frm.setVisible(true);
}
}
```

## 11.3 事件处理

### 开发程序时的实现方法

- 向事件源注册事件监听器
  - 调用事件源的addXXXListener()之类的方法。
  - 如：向按钮butt注册单击事件监听器，需要调用：
    butt.addActionListener(this);
  - 这样单击按钮时，事件监听器创建单击事件类ActionEvent对象
- 实现事件处理方法
  - 其方法体即为事件发生时要执行的语句序列

## 11.4 绘图

- Java提供了绘图类Graphics。
- 可以在组件上绘制直线、圆、圆弧、任意曲线等。
- 绘图所用的坐标系与屏幕、窗口相同。
- 水平为X轴，向右为正。
- 垂直为Y轴，向下为正。
- 原点(0,0)位于左上角。
- 点(x,y)中的x和y为距原点的水平和垂直像素。

## javax.swing中类的继承关系

![](img/80da1d99a94a92757465da523b64f0ce_492_0.png)

Swing组合框举例：窗口中有一个组合框和一个标签，当选择组合框中某项时，在标签中显示所选的信息。

```java
import java.awt.*;
import java.awt.event.*;
import javax.swing.*;
import javax.swing.event.*;
public class T1 extends JFrame{
    private JComboBox jcb;
    private JLabel jlb;
    public T1(){
        super("组合框举例");              //构造方法
        setSize(200,150);
        Object obj[]={"杭州","宁波","温州","金华","绍兴","嘉兴","湖州"};
        jcb=new JComboBox(obj);
        jcb.setMaximumRowCount(4);    //设置下拉列表框显示的最大行数
        jlb=new JLabel("");
        Container c=getContentPane();       //获得默认的内容窗格
        c.setLayout(new FlowLayout());
        c.add(jcb);
        c.add(jlb);
        jcb.addItemListener(new ItListener());   //构造方法中添加监听组合框事件
        setVisible(true);
    }
}
```

![](img/80da1d99a94a92757465da523b64f0ce_493_0.png)

```java
public static void main(String []args){
    T1 frm=new T1();
    frm.addWindowListener(new winListen());    //在main中添加监听窗口事件
}
class ItListen implements ItemListener{    //内部类,监听是否发生ItemEvent事件
    public void itemStateChanged(ItemEvent e){    //选择项目时执行
        jlb.setText("你选中了"+jcb.getSelectedItem());    //getSelectedItem():获得选项
    }
}
static class winListen extends WindowAdapter{    //内部类,监听是否发生WindowEvent事件
    public void windowClosing(WindowEvent e){    //关闭窗口时执行
        System.exit(0);    //终止程序执行
    }
}
```

![](img/80da1d99a94a92757465da523b64f0ce_494_0.png)

# 第十三章

# Applet程序

## Applet程序

- Java有两种程序
  - 独立应用程序
  - Applet程序
- Applet程序不能独立运行，必须依附于网页，借助浏览器才能运行。

## Applet简介

- Applet类
  - Applet程序继承自Java.applet.Applet类；
- 程序嵌入HTML文档中，常置于服务器端，下载到本地后由浏览器执行
- Applet类提供了Applet程序与执行环境间的标准接口，包括4个方法：
  1. init()方法：初始化。如获取Applet运行参数、加载图片等。
     它在网页第一次加载（或重新加载）时调用。
  2. start()方法：在执行init()方法后，执行start()方法。
     或该网页重新激活时，再执行start()方法。
  3. stop()方法：当离开Applet网页，使它不活动或最小时，执行该方法。
  4. destroy()方法：用户真正离开浏览器时执行。
     在stop之后执行。清除Applet占用的资源。（事实上系统会自动清除）
- Applet程序运行时，会出现一个窗口界面。当窗口大小或内容改变需要重绘窗口时，调用paint()方法。

