# 程序 3.2.4 绘制直线的双步扫描转换算法

```
void line_DoubleStep(int xs, int ys, int xe, int ye, int Color)
{ /* 设置 0 ≤ m ≤ 1/2 */
int dx = xe - xs, dy = ye - ys, current_x = xs, y = ys;
int incr_1 = 4*dy, incr_2 = 4*dy - 2*dx, d = 4*dy - dx, cond = 2*dy;
DrawPixel(current_x, y, Color);
while(current_x < xe) {
    if (d < 0) {
        DrawPixel(current_x +1, y, Color);
        DrawPixel(current_x +2, y, Color);
        d += incr_1;
    }
    else if (d < cond) {
```