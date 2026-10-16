```
for (i = 1; i <= m; i++)
    for (x = xᵢ; x <= Screen_max; x++)
        framebuffer (x, y) = A - framebuffer (x, y);
```

完成以上两步后，即完成了扫描线 y=e 上的位于多边形 P 内的像素点的奇数次求余运算，并着上了值为 P_color 的颜色。而对多边形外的像素点都做了偶数次求余运算，并着上了值为 B_color 的颜色（下图所示）。