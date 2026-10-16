# 程序 3.3.3 扫描转换圆的整数型中点算法

```
void MidpointCircle(int radius, int Color)
{
    int x, y, d;
    x = 0; y = radius; d = 1 - radius;
    CirclePoints (0, 0, x, y, Color);
    while(x < y){
        if (d < 0) { d += x*2 + 3; }
        else { d += (x - y)*2 + 5; y--; }
        x++;
        CirclePoints (0, 0, x, y, Color);
    }
}
```