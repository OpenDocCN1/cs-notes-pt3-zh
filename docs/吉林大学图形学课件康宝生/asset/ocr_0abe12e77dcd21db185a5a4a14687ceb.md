# 程序 3.2.2 DDA 扫描转换算法

```
void Line_DDA (int x0, int y0, int x1, int y1, int Color)
{
    int dy = y1 - y0, dx = x1 - x0, i, steps;
    float x = x0, y = y0, xIncrement, yincrement;
    steps = abs(dx);
    if (abs(dy) > abs(dx)) steps = abs(dy);
    xIncrement = dx /(float) steps; yIncrement = dy / (float)steps;
    DrawPixel((int)(x +0.5), (int)(y +0.5), Color);
    for (i = 1; x <= steps; i++) {
        x += xIncrement; y += yIncrement;
        DrawPixel((int)(x +0.5), (int)(y +0.5), Color);
    }
}
```