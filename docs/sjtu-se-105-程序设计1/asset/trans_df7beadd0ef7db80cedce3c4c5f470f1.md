

## Shape类

- 所有我们的shapes都是基于Shape类
  - 比如, 多边形是一种 Shape

![](img/d2d3f908f0e1c0f8ca98d9dfbe006a9f_887_0.png)

- 我们不能创建一个“普通的”Shape
  protected:
  Shape();  // protected to make class Shape abstract
  例如
  Shape ss;  // error: cannot construct Shape
  - Protected 意味着 “只能在派生类中使用”

- 相反地，我们应该使用Shape作为基类
  struct Circle : Shape {  // “a Circle is a Shape”
  // ...
  };

- Shape 将我们的图形对象联系到屏幕上
  - Window “知道” Shape
  - 所有的图形对象都是某种Shape
- Shape 是一个类，用来处理颜色和风格
  - 它有 Color 和 Line_style 两个成员
- Shape 可以持有多个点(Point)
- Shape 包含如何绘制直线的基本概念
  - Shape 将其持有的Point 连接起来

- Shape 处理颜色和风格
  - 它保持其数据的私有性，并提供访问函数
    void set_color(Color col);
    Color color() const;
    void set_style(Line_style sty);
    Line_style style() const;
    // ...
    private:
    // ...
    Color line_color;
    Line_style ls;

- Shape 存储点(Points)
  - 它保持数据的私有化和提供访问函数
    Point point(int i) const;      // read-only access to points
    int number_of_points() const;
    // ...
  protected:
    void add(Point p);      // add p to points
    // ...
  private:
    vector<Point> points;      // not used by all shapes

## Shape类

- Shape 本身可以直接访问点(point):

```
void Shape::draw_lines() const        // draw connecting lines
{
    if (color().visible() && 1<points.size())
        for (int i=1; i<points.size(); ++i)
            fl_line(points[i-1].x,points[i-1].y,points[i].x,points[i].y);
}
```

- 其他类(含派生类) 需要使用 point() 和number_of_points()
  - 为什么？

```
void Lines::draw_lines() const        // draw a line for each pair of points
{
    for (int i=1; i<number_of_points(); i+=2)
        fl_line(point(i-1).x, point(i-1).y, point(i).x, point(i).y);
}
```

## Shape类 (绘图的基本思路)

```
void Shape::draw() const
// Shape类的真正核心函数 (同时也是我们图形界面系统的核心)
// 只能由 Window 调用
{
// ... save old color and style ...
// ... set color and style for this shape...

// ... draw what is specific for this particular shape ...
// ... Note: this varies dramatically depending on the type of shape ...
// ... e.g. Text, Circle, Closed_polyline

// ... reset the color and style to their old values ...
}
```

## Shape类 (绘图的实现)

```
void Shape::draw() const
// The real heart of class Shape (and of our graphics interface system)
// called by Window (only)
{
    Fl_Color oldc = fl_color();      // save old color
    // there is no good portable way of retrieving the current style (sigh!)
    fl_color(line_color.as_int());   // set color and style
    fl_line_style(ls.style(),ls.width());

    draw_lines(); // call the appropriate draw_lines()
                  // a “virtual call”
                  // here is what is specific for a “derived class” is done

    fl_color(oldc);      // reset color to previous
    fl_line_style(0);    // (re)set style to default
}
```

## Shape类

- Shape类
  virtual void draw_lines() const;  // draw the appropriate lines
- Circle类
  void draw_lines() const { /* draw the Circle */ }
- Text 类
  void draw_lines() const { /* draw the Text */ }
- Circle、Text 和其他的类
  - “派生自” Shape
  - 可以 “覆盖” draw_lines()

## Shape类

```
class Shape {      // deals with color and style, and holds a sequence of lines
public:
    void draw() const;                     // deal with color and call draw_lines()
    virtual void move(int dx, int dy); // move the shape +=dx and +=dy

    void set_color(Color col);            // color access
    int color() const;
    // ... style and fill_color access functions ...

    Point point(int i) const;             // (read-only) access to points
    int number_of_points() const;
protected:
    Shape();                              // protected to make class Shape abstract
    void add(Point p);                    // add p to points
    virtual void draw_lines() const;      // simply draw the appropriate lines
private:
    vector<Point> points;                 // not used by all shapes
    Color lcolor;                         // line color
    Line_style ls;                        // line style
    Color fcolor;                         // fill color
    // ... prevent copying ...
};
```
