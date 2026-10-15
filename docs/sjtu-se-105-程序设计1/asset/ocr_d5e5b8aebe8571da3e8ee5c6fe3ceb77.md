# Demo code 7

+   - 填充与线型

```
r.set_fill_color(Color::yellow);    // color the inside of the rectangle
poly.set_style(Line_style(Line_style::dash,4));    // make the triangle fat

poly_rect.set_fill_color(Color::green);
poly_rect.set_style(Line_style(Line_style::dash,2));

win.set_label("Canvas #7");
```