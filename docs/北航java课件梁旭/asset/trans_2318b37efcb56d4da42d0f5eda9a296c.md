

## GridLayout布局管理器

- GridLayout类有三种构造方法：
- public GridLayout()
  在一行中放置所有的组件，各组件间的水平间距为0像素。
- public GridLayout(int rows, int cols)
  生成一个rows行，cols列的管理器，最多能放置 rows*cols 个组件。（课本有误）。
  rows或cols可以有一个为0。若rows为0，这表示每行放置cols个组件，根据具体组件数，可以有任意多行；若cols为0，这表示共有rows行，根据具体组件数，每行可以放置任意多个组件。
  组件间的水平和竖直间距为0像素。
- public GridLayout(int rows, int cols, int horizontalGap, int verticalGap )
  各组件间的水平和竖直间距为指定值。

## CardLayout布局管理器

CardLayout布局方式可以帮助用户处理两个或更多的组件共享同一显示空间。共享空间的组件之间的关系就像一摞牌一样，它们摞在一起，只有最上面的组件是可见的。CardLayout可以象牌一样处理这些共享空间的组件；为每张牌定义一个名字，可按名字选牌；可以按顺序向前或向后翻牌；也可以直接选第一张或最后一张牌。类似于VB中的选项卡。

- 常用方法：
- `public void show(Container parent, String name)`
  //显示指定名称的卡片
- `public void next(Container parent)`
- `public void previous(Container parent)`
- `public void first(Container parent)`
- `public void last(Container parent)`
- 其中，Container是拥有该CardLayout布局管理器的容器。

## CardLayout布局管理器

- CardLayout类有两种构造方法：
- public CardLayout()
- 组件距容器左右边界和上下边界的距离为缺省值0个像素。
- public CardLayout(int horizontalGap, int verticalGap)
- 组件距容器左右边界和上下边界的距离为指定值。
- 与BorderLayout类和GridLayout类相类似，每张牌中只能放置一个组件，如果想在一张牌放置多个组件，则必须先在该牌放一个容器，再将多个组件放在该容器中。
- 采用CardLayout布局方式时，向容器中添加组件时可以为组件取一个名字，以供更换显示组件时使用：
- add(String, Component);

## GridBagLayout布局管理器

GridBagLayout布局方式是AWT中最灵活、同时也是最复杂的一种布局方式。与GridLayout相同，它也是将容器中的组件按照行、列的方式放置，但各组件所占的空间可以互不相同。

GridBagLayout根据对每个组件所施加的空间限制、每个组件自身所设定的最小尺寸和最佳尺寸来为每个组件分配空间。对组件施加空间限制是通过类GridBagConstraints来实现的。

## GridBagLayout布局管理器

类GridBagConstraints中提供了一些相应的属性和常量来设置对组件的空间限制：
- gridx, gridy
  //指明组件显示区域左上角坐标（在容器中）
- gridwidth, gridheight
  //指明组件在一行中所占的网格单元数（宽度，高度）。
- fill //指明当组件所在的网格单元的区域大于组件所请求的区域时，是否改变组件的尺寸
- ipadx, ipady
  //指明组件的宽/高度与指定的最小宽/高度之间的关系
- insets //指明了组件与其显示区边缘之间的距离
- anchor
  //指明了当组件的尺寸小于其显示区时，在显示区中如何放置改组件的位置
- weightx, weighty
  //指明当容器扩大时，如何在列，行间为组件分配额外的空间

## GridBagLayout布局管理器

当一个容器的布局方式为GridBagLayout时，往其中添加一个组件，必须先用GridBagConstraints设置该组件的空间限制。

- //在一个容器中
- GridBagLayout g = new GridBagLayout();
- GridBagConstraints c = new GridBagConstraints();
- setLayout( g );
- Button b = new Button("Test");  //生成组件b
- c.fill = ...  //设置c的值
- ......
- g.setConstraints( b, c );  //根据c的值对组件b进行空间限制
- add( b );

## Swing布局管理器

- Swing除了可用上述五种布局管理器外，还提供其他选择。其中：
- ScrollPanelLayout和ViewportLayout是内置的。
- BoxLayout和OverlayLayout的使用类似AWT的布局管理器。
- BoxLayout
- ScrollPanelLayout
- 详见javax.swing包中。

## null布局管理器

- 用户不想使用布局管理器，需要自己设置组件的位置和大小，需取消布局管理器，然后再进行设置，否则用户自定义的设置将会被布局管理器覆盖。
- 取消方法：
  setLayout(null)
- 设置方法：
  setLocation()
  setSize()
  setBounds()方法
- 注：这种方法会导致程序的运行效果与系统有关。
- 用户也可以通过实现LayoutManager接口来定义自己的布局管理器。

## 8.4 事件处理

- 事件是由程序检测到的行为和动作。
- 事件是发生在用户界面上的用户交互行为所产生的一种效果。
- 事件是系统对其可能处于的某种状态或者某种操作的预先定义。
- Java采用一种叫“事件授权模型”的事件处理机制，即委托型事件处理模式。当用户与GUI程序交互时，会触发相应的事件。
- 事件源：产生事件的组件称为事件源。
- 监听器：触发事件后系统会自动创建事件类的对象，组件本身不会处理事件，而是将事件对象提交给Java运行时系统，系统将事件对象委托给专门的实体——监听器。
- 事件源与监听器建立联系的方式是将监听器注册给事件源。

## 8.4.1 java的事件类

![](img/b58cead0522d3247058937ec2b7b313c_226_0.png)

## 8.4.1 java的事件类

- 事件都放在包java.awt.event中，这些事件都从java.util.Event对象派生而来，对于与AWT有关的事件，则由java.awt.AWTEvent类派生，可分为两大类：
- 低级事件：基于构件和容器的事件。
  - ComponentEvent，构件尺寸的变化、移动。
  - ContainerEvent，容器事件，构件增加、移动。
  - WindowEvent，窗口事件，关闭，还原，最小化。
  - FocusEvent，焦点事件，焦点的获得和丢失。
  - KeyEvent，键盘事件，键按下、释放。
  - MouseEvent，鼠标事件，鼠标单击、移动。
- 高级事件（语义事件，可以不和特定的动作相关联，而依赖于触发此事件的类。一般的GUI编程，只需对这类事件进行处理即可）
  - ActionEvent，动作事件，按下按钮或按下文本框中的回车键产生。
  - AdjustmentEvent，调节事件，用户在滚动条上移动滑块产生。
  - ItemEvent，项目事件，选择项目等产生。
  - TextEvent，文本事件，文本对象的改变。

## 8.4.2 事件处理模式

一个Java事件处理模型的具体步骤：

- 1. 创建事件监听器
- 2. 注册事件监听器
- 3. 创建事件对象
- 4. 通知事件发生
- 5. 执行事件处理程序

## 8.4.2 事件处理模式

事件处理过程中主要涉及3类对象：

- Event：事件，用户对界面操作在Java语言上的描述，以类的形式出现。
- Event Source：事件源，事件发生的场所，通常就是各个构件。
- Event Handler：事件处理者（监听器），接收事件对象并对其进行处理的对象。

