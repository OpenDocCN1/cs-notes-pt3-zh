

## 8.1 图形用户界面设计概述

通过图形用户界面（Graphical User Interface，GUI），用户和程序之间可以方便友好地进行交互。在Java语言中，Java的基础类（Java Foundation Classes，JFC）是开发GUI的API集，它包括以下几个部分：

- 抽象窗口工具包（AWT）：Java开发用户界面最初的工具包，是建立JFC的主要基础；
- 2D API：实现高质量的二维图形；
- Swing组件：建立在AWT之上，新的、功能更强大的图形组件包；
- etc.

## 8.2 AWT图形用户界面

- 图形用户界面（GUI）使用户可以和程序进行可视化交互。
- 图形用户界面包含了许多独立的显示元素，供用户交互。它们由程序中的GUI组件组成。GUI组件是用户通过键盘或鼠标进行交互的对象，菜单、按钮、文本域、标签和下拉列表框等GUI组件是图形用户界面的常用部分。
- AWT (Abstract Window Toolkit)用来处理GUI的最基本方式，可用来创建Applet和窗口，支持GUI编程的主要功能。

### 8.2.1 java.awt包

java.awt及相关包中包含了一个完整的类集以支持GUI程序的设计，其中的类及相互关系可以用下图来描述（重量级构件）：

![](img/b58cead0522d3247058937ec2b7b313c_203_0.png)

### 8.2.2 构件和容器类

- 一、构件类（Component类）

  最核心的类，它是构成Java图形用户界面的基础，大部分构件都是由该类派生出来的。

  Component类是一个抽象类，其中定义了构件所具有的一般功能（方法）：

  - 基本的绘画支持(paint, repaint, update等);
  - 字体和颜色等外形控制(setFont, setForeground等);
  - 大小和位置控制(setSize, setLocation等);
  - 图像处理(实现接口ImageObserver);
  - 组件状态控制(setEnable, setVisible, isEnabled, isValid等)
  - 获得构件对象(getComponentAt, getName, getFont, getForeground, getSize等)

  常见的构件包括：Button, Checkbox, CheckboxGroup, Choice, Label, List, Canvas, TextComponent, Scrollbar等。

- 二、容器类(Container)

  Container类是由Component类派生出来的一种特殊子类，用来表示各种GUI构件的容器，可以容纳多个构件，其主要功能包括：

  - 构件的管理：方法add()可以向其中添加一个构件，remove()删除其中的一个构件，...
  - 布局管理：每个Container类都和一个布局管理器相联，以确定其中构件的布局。Container类可以通过setLayout()方法设置某种布局方式。

  常见的Container类有：Frame, Panel, Applet等。

- 三、布局管理器类

  用来管理构件放置在容器中的位置和大小。每个容器都有一个布局管理器，当容器需要对某个构件进行定位或判断其大小尺寸时，就会调用其对应的布局管理器。为保证GUI的平台无关性，不能使用直接设置构件位置和大小的方式。

### 常用容器类(Container)

- 1、窗口（Frame）

  在Java中，生成一个窗口通常是用Window的子类Frame来进行实例化，不直接用Window类。

  生成的窗口，如果不添加响应代码，不能响应用户的操作，如“关闭窗口”等。

  例:

  ```java
  public class li81 extends Frame{
      public static void main(String args[]){
          li81 fr=new li81("This is a container");//窗口名
      }
  }
  ```

- 2、面板（Panel）

  透明容器，无标题，无边框。

  既是容器，又是构件。必须先作为构件放到其他容器中，然后再当容器容纳其他构件。

  ```java
  Panel pan=new Panel();
  ```

## 8.3 布局管理

Java中提供了各种布局管理器类来管理各种组件在容器中的放置状态，这些类都是实现了LayoutManager接口的。标准的布局管理器类(在java.awt包中)有：

- FlowLayout
- BorderLayout
- GridLayout
- CardLayout
- GridBagLayout

还可以通过实现LayoutManager接口来定义自己的布局管理器。

### FlowLayout布局管理器

- Panel和Applet的缺省布局管理器

- FlowLayout布局方式: 将组件一排一排地依次放置，它自动调用组件的 getPreferredSize()方法，使用组件的最佳尺寸来显示组件。当容器被重新设置大小后，布局也会随之发生改变：各组件的大小不变，但相对位置会发生变化。

- 组件配置过程:

  (1) 由左到右配置在长方形格子里；

  (2) 格子大小为组件大小；

  (3) 配置完一行，再配置下一行，直到组件配置完成。

- FlowLayout类有三种构造方法,即声明方式有三：
  - public FlowLayout()
    使用缺省居中对齐方式，组件间的水平和竖直间距为缺省值5个像素。
  - public FlowLayout(int alignment)
    使用指定的对齐方式（FlowLayout.LEFT，FlowLayout.RIGHT，FlowLayout.CENTER），水平和竖直间距为缺省值5像素。
  - public FlowLayout(int alignment, int horizontalGap, int verticalGap)
    使用指定的对齐方式，水平和竖直间距也为指定值。

### BorderLayout布局管理器

- Window、Dialog和Frame的缺省布局管理器

- BorderLayout布局方式提供了更复杂的布局控制方法，它包括5个区域：North, South, East, West和Center，其方位依据上北下南左西右东。当容器的尺寸发生变化时，各组件的相对位置不变，但中间部分组件的尺寸会发生变化，南北组件的高度不变，东西组件的宽度不变。

- BorderLayout类有两种构造方法：
  - public BorderLayout()
    各组件间的水平和垂直间距为缺省值0个像素。
  - public BorderLayout(int horizontalGap, int verticalGap)
    各组件间的水平和垂直间距为指定值。

- 如果容器使用了BorderLayout布局方式，则用add()方法往容器中添加组件时必须指明添加的位置，否则组件将无法正确显示（不同的布局管理器，向容器中添加组件的方法也不同）。

  如：

  ```java
  add("West", new Button("West"));
  add("North", new Button("North"));
  add(new Button("West"), BorderLayout.SOUTH);
  ```

  若没有指明放置位置，则表明为默认的“Center”方位。

- 每个区域只能添加一个组件，若添加多个，则只能显示一个。如果想在一个区域添加多个组件，则必须先在该区域放一个Panel容器，再将多个组件放在该Panel容器中。

- 若每个区域或若干个区域没有放置组件，东西南北区域将不会有预留，而中间区域将置空。

### GridLayout布局管理器

- GridLayout布局方式可以使容器中的各组件呈网格状分布。容器中各组件的高度和宽度相同，当容器的尺寸发生变化时，各组件的相对位置不变，但各自的尺寸会发生变化。
- 各组件的排列方式：从左到右，从上到下。
- 与BorderLayout类相似，如果想在一个网格单元中添加多个组件，则必须先在该网格单元放一个Panel容器，再将多个组件放在该Panel容器中。

![](img/b58cead0522d3247058937ec2b7b313c_215_0.png)

