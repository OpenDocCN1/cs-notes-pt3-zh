# 颜色模式转换（Color Space Transformation）

+   - RGB -> YCbCr色彩系统（Y 亮度brightness， Cb, Cr代表色度chrominance(分别对于蓝色和红色)）

```
Y' =     0.299·R' +     0.587·G' +     0.114·B'
P_B = -  0.168736·R' -  0.331264·G' +       0.5·B'
P_R =       0.5·R' -  0.418688·G' -  0.081312·B'
```