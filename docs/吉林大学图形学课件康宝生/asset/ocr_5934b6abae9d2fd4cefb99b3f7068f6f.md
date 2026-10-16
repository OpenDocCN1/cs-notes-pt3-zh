```
while (code1 != 0 || code2 != 0)
{
    if (code1 & code2 != 0) return;
    if ( code1 != 0) code = code1;
    else code = code2;
    if (LEFT & code != 0) { // 点在窗口左边界左侧
        x = XL;
        y = y1 + (y2 - y1) * (XL - x1)/(x2 - x1);
    }
    else if (RIGHT & code != 0) { // 点在窗口右边界右侧
        x = XR;
        y = y1 + (y2 - y1) * (XR - x1)/(x2 - x1);
    }
    else if (BOTTOM & code != 0) { // 点在窗口下边界下方
```