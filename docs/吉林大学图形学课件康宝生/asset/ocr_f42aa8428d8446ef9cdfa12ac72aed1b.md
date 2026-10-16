（3）根据像素的移动情况，用前面计算的差分常量修改 D_E 或 D_SE；（4）移动像素。D_E 或 D_SE 使用起始像素进行初始化。改进后的程序如程序 3.3.4 所示。

# 程序 3.3.4 基于二阶差分的中点圆扫描转换算法

```
void MidpointCircle (int radius, int Color)
{
    int x, y, d, deltaE, deltaSE;
    x = 0; y = radius; d = 1 - radius; deltaE = 3; deltaSE = 5 - radius*2;
    CirclePoints (0, 0, x, y, Color);
    while( x < y ) {
        if (d < 0) {
```