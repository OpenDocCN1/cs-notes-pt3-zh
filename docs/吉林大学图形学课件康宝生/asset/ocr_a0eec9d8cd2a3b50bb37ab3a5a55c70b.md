设 G 是内点表示的区域，(x,y) 是 G 内的种子点。G 的原色是 Old_Color，填充色为 F_Color。泛填充算法的原理是：从种子点 (x,y) 开始，置 (x,y) 的颜色为填充色 F_Color，而后使用4-连通方法或 8-连通方法，逐步连通各像素点，直到所有内部像素点均已被涂上填充色为止。

# 程序 3.4.2 区域填充的边界算法

```
void floodFill4 (int x, int y, int F_Color, int Old_Color)
{
    if (GetPixel (x, y) === Old_Color) {
        DrawPixel (x, y, F_Color);
```