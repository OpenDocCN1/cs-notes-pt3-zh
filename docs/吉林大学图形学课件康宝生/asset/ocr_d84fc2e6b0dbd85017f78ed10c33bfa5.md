# GetPixel(x, y)

又设 interior_Point 为布尔变量，在搜索过程中，如果当前像素点位于多边形 P 内，则 interior_Point = 1，需着上值为 P_color 的颜色。否则，该像素点在多边形 P 外，需着上值为 B_color 的颜色。这一步的程序框架如下：

```
for (y = Screen_ymin; y <= Screen_ymax; y++) {
    interior_Point =0;
    for (x = Screen_xmin; x <= Screen_xmax; x++) {
        if (GetPixel (x, y) === B_color) interior_Point = ! interior_Point;
        if (interior_Point) DrawPixel (x, y, P_color);
    }
}
```