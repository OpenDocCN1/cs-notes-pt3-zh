# 014：XAML乒乓球游戏-part2

![](img/8a4c893755b14b0e6bd2267e1a5a46ff_1.png)

在本节课中，我们将继续构建XAML乒乓球游戏。我们将学习如何将游戏部署到Xbox，并重构代码以使用接口来管理可绘制和可碰撞的对象，从而让游戏逻辑更清晰、更易于扩展。

![](img/8a4c893755b14b0e6bd2267e1a5a46ff_3.png)

---

## 部署到Xbox 🎮

上一节我们介绍了游戏的基本框架，本节中我们来看看如何将游戏部署到Xbox上进行测试。

要连接到Xbox，你的设备必须连接到M无线网络，而不是访客网络。在Visual Studio的右下角，选择“远程计算机”并输入Xbox的IP地址。首次连接时，需要在Xbox屏幕上输入Visual Studio提供的PIN码进行配对。

在Xbox上，你需要进入开发者模式。具体步骤是：在“设置”中进入“主机信息”->“开发者设置”。如果未显示该选项，可以尝试同时按下左缓冲键、右缓冲键、左扳机键和右扳机键来激活开发者设置界面。此外，你还需要登录一个Xbox账户。

部署时，请确保项目配置为64位（例如`x64`），因为Xbox不支持x86目标。部署过程可能需要一些时间。成功部署后，游戏窗口将出现在Xbox屏幕上。

**注意**：默认情况下，按Xbox控制器的B键会关闭应用。在后续添加控制器支持时，请记得为B键绑定其他功能，否则误按会导致应用退出。

为了在Xbox上获得更好的体验，我们可以在XAML中禁用鼠标指针。在`App.xaml`文件中添加以下属性：
```xml
RequiresPointerMode="WhenRequested"
```

---

## 使用接口重构绘图逻辑 🖌️

![](img/8a4c893755b14b0e6bd2267e1a5a46ff_5.png)

目前，我们直接在游戏循环中绘制每个对象（如墙壁、球）。为了使代码更模块化、更容易添加新对象，我们将引入一个`IDrawable`接口。

![](img/8a4c893755b14b0e6bd2267e1a5a46ff_7.png)

![](img/8a4c893755b14b0e6bd2267e1a5a46ff_9.png)

`IDrawable`接口定义了一个`Draw`方法，任何实现该接口的类都必须提供如何绘制自己的逻辑。

以下是`IDrawable`接口的定义：
```csharp
public interface IDrawable
{
    void Draw(CanvasDrawingSession session);
}
```

然后，我们可以让`Rectangle`和`Circle`类实现这个接口。例如，`Rectangle`类的`Draw`方法会调用`session.DrawRectangle()`，而`Circle`类的`Draw`方法会调用`session.DrawCircle()`。

在游戏主类中，我们可以维护一个`IDrawable`对象的列表：
```csharp
List<IDrawable> drawables = new List<IDrawable>();
```

将所有游戏对象（左墙、右墙、球）添加到这个列表中。在游戏循环的绘制阶段，我们只需遍历这个列表并调用每个对象的`Draw`方法即可：
```csharp
foreach (IDrawable drawable in drawables)
{
    drawable.Draw(session);
}
```

![](img/8a4c893755b14b0e6bd2267e1a5a46ff_11.png)

这种方法的好处是，未来添加任何新类型的可绘制对象（如砖块、道具），只需让它实现`IDrawable`接口并添加到列表中，无需修改游戏循环的核心绘制代码。

![](img/8a4c893755b14b0e6bd2267e1a5a46ff_13.png)

---

![](img/8a4c893755b14b0e6bd2267e1a5a46ff_15.png)

![](img/8a4c893755b14b0e6bd2267e1a5a46ff_17.png)

## 实现碰撞检测 💥

为了让球与墙壁和球拍发生交互，我们需要实现碰撞检测。我们将创建一个`ICollidable`接口来定义可碰撞对象的行为。

`ICollidable`接口需要提供获取对象边界（左、右、上、下边缘）的属性，以及一个检测与另一个`ICollidable`对象是否发生碰撞的方法。

![](img/8a4c893755b14b0e6bd2267e1a5a46ff_19.png)

![](img/8a4c893755b14b0e6bd2267e1a5a46ff_21.png)

以下是`ICollidable`接口的一个示例定义：
```csharp
public interface ICollidable
{
    int LeftEdgeX { get; }
    int RightEdgeX { get; }
    int TopEdgeY { get; }
    int BottomEdgeY { get; }

    bool DidCollideWith(ICollidable other);
}
```

![](img/8a4c893755b14b0e6bd2267e1a5a46ff_23.png)

![](img/8a4c893755b14b0e6bd2267e1a5a46ff_25.png)

`Rectangle`类可以轻松实现这个接口，因为它的边界是矩形。对于`Circle`类，我们可以用一个外接矩形来近似其碰撞区域，以简化计算。

碰撞检测的逻辑基于“分离轴定理”。对于两个矩形，如果其中一个的右边缘在另一个的左边缘左侧，或者左边缘在另一个的右边缘右侧，或者类似地在垂直方向上分离，则它们没有碰撞。否则，它们发生了碰撞。

![](img/8a4c893755b14b0e6bd2267e1a5a46ff_27.png)

![](img/8a4c893755b14b0e6bd2267e1a5a46ff_29.png)

以下是`DidCollideWith`方法的一种实现方式：
```csharp
public bool DidCollideWith(ICollidable other)
{
    // 检查是否没有碰撞（分离）
    if (this.RightEdgeX <= other.LeftEdgeX ||
        this.LeftEdgeX >= other.RightEdgeX ||
        this.BottomEdgeY <= other.TopEdgeY ||
        this.TopEdgeY >= other.BottomEdgeY)
    {
        return false;
    }
    // 否则为碰撞
    return true;
}
```

![](img/8a4c893755b14b0e6bd2267e1a5a46ff_31.png)

![](img/8a4c893755b14b0e6bd2267e1a5a46ff_33.png)

在游戏更新逻辑中，我们检查球（一个`ICollidable`）是否与任何其他`ICollidable`对象（如墙壁、球拍）发生碰撞。如果发生碰撞，则根据碰撞对象类型改变球的运动方向（水平反弹或垂直反弹）。

为了更精细地控制，我们可以将可碰撞对象分为两组：影响水平运动的（如左右墙）和影响垂直运动的（如上下球拍）。这样，球撞到球拍时只会改变垂直方向，撞到墙壁时只会改变水平方向。

---

## 添加球拍与玩家控制 🎮

现在，让我们添加球拍并允许玩家控制其中一个。

![](img/8a4c893755b14b0e6bd2267e1a5a46ff_35.png)

![](img/8a4c893755b14b0e6bd2267e1a5a46ff_37.png)

首先，创建两个`Rectangle`对象作为顶部和底部的球拍，并将它们添加到`drawables`列表和相应的`ICollidable`列表中。

为了让玩家控制底部的球拍，我们需要处理键盘输入。在XAML页面构造函数中，注册`KeyDown`和`KeyUp`事件：
```csharp
this.KeyDown += MainPage_KeyDown;
this.KeyUp += MainPage_KeyUp;
```

![](img/8a4c893755b14b0e6bd2267e1a5a46ff_39.png)

在事件处理程序中，设置标志位来跟踪玩家是否按下了左键或右键：

![](img/8a4c893755b14b0e6bd2267e1a5a46ff_41.png)


![](img/8a4c893755b14b0e6bd2267e1a5a46ff_43.png)

![](img/8a4c893755b14b0e6bd2267e1a5a46ff_45.png)

```csharp
private bool userPaddleGoingLeft = false;
private bool userPaddleGoingRight = false;
private void MainPage_KeyDown(object sender, KeyRoutedEventArgs e)
{
    if (e.Key == Windows.System.VirtualKey.Left)
    {
        userPaddleGoingLeft = true;
    }
    else if (e.Key == Windows.System.VirtualKey.Right)
    {
        userPaddleGoingRight = true;
    }
}
private void MainPage_KeyUp(object sender, KeyRoutedEventArgs e)
{
    if (e.Key == Windows.System.VirtualKey.Left)
    {
        userPaddleGoingLeft = false;
    }
    else if (e.Key == Windows.System.VirtualKey.Right)
    {
        userPaddleGoingRight = false;
    }
}
```

![](img/8a4c893755b14b0e6bd2267e1a5a46ff_47.png)

![](img/8a4c893755b14b0e6bd2267e1a5a46ff_49.png)

在游戏更新循环中，根据这些标志位移动底部球拍。同时，在移动前检查球拍是否会与左右墙壁碰撞，以防止它移出屏幕：
```csharp
if (userPaddleGoingLeft && !bottomPaddle.DidCollideWith(leftWall))
{
    bottomPaddle.X--;
}
if (userPaddleGoingRight && !bottomPaddle.DidCollideWith(rightWall))
{
    bottomPaddle.X++;
}
```

对于顶部的球拍，我们可以先实现简单的AI，例如让它的X坐标跟随球的X坐标，模拟一个电脑对手。

---

![](img/8a4c893755b14b0e6bd2267e1a5a46ff_51.png)

## 完善游戏逻辑与总结 🏓

![](img/8a4c893755b14b0e6bd2267e1a5a46ff_53.png)

目前，我们的球可以左右移动并与墙壁碰撞，也可以上下移动并与球拍碰撞。基本的乒乓球游戏框架已经搭建起来。

![](img/8a4c893755b14b0e6bd2267e1a5a46ff_55.png)

![](img/8a4c893755b14b0e6bd2267e1a5a46ff_56.png)

![](img/8a4c893755b14b0e6bd2267e1a5a46ff_58.png)

然而，还有很多可以完善的地方：
1.  **计分与游戏结束**：当球飞出顶部或底部边界时，给对方加分，并重置球的位置。
2.  **更真实的物理**：根据球击中球拍的不同位置，改变反弹的角度和速度。
3.  **页面导航**：添加开始菜单、游戏说明、制作人员名单等页面。
4.  **图像与音效**：用图片替换简单的几何图形，并添加游戏音效。
5.  **代码结构优化**：将游戏逻辑封装到一个独立的`Game`或`Pong`类中，使UI代码与游戏逻辑分离，更易于管理。

本节课中我们一起学习了如何将游戏部署到Xbox，以及如何使用`IDrawable`和`ICollidable`接口来重构代码，使游戏对象的管理和碰撞检测更加清晰和可扩展。我们还实现了玩家控制的球拍和基础的碰撞反弹逻辑。

![](img/8a4c893755b14b0e6bd2267e1a5a46ff_60.png)

![](img/8a4c893755b14b0e6bd2267e1a5a46ff_61.png)

在接下来的课程中，我们将学习如何加载图像和音效，并进一步优化游戏结构，为最终完成一个完整的游戏项目做好准备。