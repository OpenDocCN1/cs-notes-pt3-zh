
## 用图绘制数据

![](img/d2d3f908f0e1c0f8ca98d9dfbe006a9f_952_0.png)

- 仔细设计我们的屏幕布局

## 关于坐标轴的代码

```cpp
struct Axis : Shape {
    enum Orientation { x, y, z };
    Axis(Orientation d, Point xy, int length,
        int number_of_notches=0,    // default: no notches
        string label = ""          // default : no label
    );

    void draw_lines() const;
    void move(int dx, int dy);

    void set_color(Color); // in case we want to change the color of all parts at once

    // line stored in Shape
    // orientation not stored (can be deduced from line)
    Text label;
    Lines notches;
};
```

```cpp
Axis::Axis(Orientation d, Point xy, int length, int n, string lab)
:label(Point(0,0),lab)
{
    if (length<0) error("bad axis length");
    switch (d){
    case Axis::x:
    {
        Shape::add(xy);                         // axis line begin
        Shape::add(Point(xy.x+length,xy.y));    // axis line end
        if (1<n) {
            int dist = length/n;
            int x = xy.x+dist;
            for (int i = 0; i<n; ++i) {
                notches.add(Point(x,xy.y),Point(x,xy.y-5));
                x += dist;
            }
        }
        label.move(length/3,xy.y+20);  // put label under the line
        break;
    }
    // ...
}
```

## GUI 概览

- 内容
  - 输入/输出 I/O
  - 图形用户界面 GUI
  - 软件的分层
- GUI 例子
- GUI 代码
  - 回调函数

- 标题 / 文本
  - 名字
  - 提示
  - 用户说明
- 域 / 对话框
  - 输入
  - 输出
- 按钮
  - 让用户激发动作
  - 让用户在一组选项中选择
    - 比如：是/否，蓝/绿/红，等等。

## 常见的图形用户界面任务

- 显示结果
  - 形状
  - 文本和数字
- 使窗口“看起来恰当”
  - 风格和颜色
    - 注意：我们的窗口在不同的系统中看起来是不同的并且是恰当的
- 更高级的操作
  - 跟踪鼠标
  - 拖放
  - 手绘

- 从编程的角度来看，图形用户界面是基于两种技术
  - 面向对象编程
    - 负责用通用接口和通用动作将各个程序部分组织在一起
  - 事件
    - 负责将一个事件（比如鼠标点击）和程序动作联系起来

## 软件分层

![](img/d2d3f908f0e1c0f8ca98d9dfbe006a9f_961_0.png)

![](img/d2d3f908f0e1c0f8ca98d9dfbe006a9f_961_1.png)

## 层的实例

- 提供服务
- 使用服务

- 窗口
  - 有两个按钮Button、两个输入框In_box和一个输出框Out_box

![](img/d2d3f908f0e1c0f8ca98d9dfbe006a9f_962_0.png)

## GUI 实例

![](img/d2d3f908f0e1c0f8ca98d9dfbe006a9f_963_0.png)

- 在输入框In_box中输入一个点

![](img/d2d3f908f0e1c0f8ca98d9dfbe006a9f_964_0.png)

- 当用户点击 ‘next point’ 按钮时候，这个当前的位置变成(x,y)，同时在输出框Out_box中显示

![](img/d2d3f908f0e1c0f8ca98d9dfbe006a9f_965_0.png)

- 添加另外的点，这样就形成了一条直线

![](img/d2d3f908f0e1c0f8ca98d9dfbe006a9f_966_0.png)

- 三个点就形成了两条线
  - 显然，我们在构造折线

![](img/d2d3f908f0e1c0f8ca98d9dfbe006a9f_967_0.png)

- 以此类推，直到点击 Quit 为止

## 界面元素和实现

- 我们在窗口中看到按钮，输入框和输出框
  - 我们如何定义一个窗口？
  - 我们如何定义按钮？
  - 我们如何定义输入框和输出框？
- 点击按钮，然后相应事件发生
  - 我们如何对动作进行编码？
  - 我们如何将代码和按钮连接到一起？
- 用户在输入框中输入信息
  - 我们如何在代码中得到输入的信息？
  - 我们如何将字符串转换成数字？
- 我们看到了输出框里的输出
  - 我们如何将值输出到那里？
- 线段出现在窗口中
  - 我们如何保存线段？
  - 我们如何绘制线段？

## 映射

- 我们将自己的想法映射到传统的图形/GUI思想的FLTK版本上

```cpp
struct Lines_window : Window    // Lines_window inherits from Window
{
    Lines_window(Point xy, int w, int h, const string& title); // declare constructor
    Open_polyline lines;

private:
    Button next_button;                // declare some buttons – type Button
    Button quit_button;
    In_box next_x;                     // declare some i/o boxes
    In_box next_y;
    Out_box xy_out;

    void next();                       // what to do when next_button is pushed
    void quit();                       // what to do when quit_button is pushed

    static void cb_next(Address, Address window);    // callback for next_button
    static void cb_quit(Address, Address window);    // callback for quit_button
};
```

![](img/d2d3f908f0e1c0f8ca98d9dfbe006a9f_971_0.png)

- 窗口
  - 有两个按钮、两个输入框和一个输出框

## Lines_window 构造函数

```cpp
Lines_window::Lines_window(Point xy, int w, int h, const string& title)
:Window(xy,w,h,title),
    // construct/initialize the parts of the window:
    // location        size        name        action
    next_button(Point(x_max()-150,0), 70, 20, "Next point", cb_next),
    quit_button(Point(x_max()-70,0), 70, 20, "Quit", cb_quit),    // quit button
    next_x(Point(x_max()-310,0), 50, 20, "next x:"),                // io boxes
    next_y(Point(x_max()-210,0), 50, 20, "next y:"),
    xy_out(Point(100,0), 100, 20, "current (x,y):")
{
    attach(next_button);    // attach the parts to the window
    attach(quit_button);
    attach(next_x);
    attach(next_y);
    attach(xy_out);
    attach(lines);          // attach the open_polylines to the window
}
```
