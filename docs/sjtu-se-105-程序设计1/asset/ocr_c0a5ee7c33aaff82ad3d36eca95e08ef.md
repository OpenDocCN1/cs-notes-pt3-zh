```
Circle c(Point(100,200),50);

Ellipse e(Point(100,200), 75,25);
e.set_color(Color::dark_red);

Mark m(Point(100,200),'x');

ostringstream oss;
oss << "screen size: " << x_max() << "*" << y_max() << "; window size: " << win.x_max() << "*" << win.y_max();
Text sizes(Point(100,20),oss.str());

Image cal(Point(225,225),"snow_cpp.gif"); // 320*240 pixel gif
cal.set_mask(Point(40,40),200,150);                // display center of image

win.set_label("Canvas #12");
win.wait_for_button();
```