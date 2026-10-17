# 2) James D.Foley 描述描述

```
void Line ( //设 0≤k≤1,xs<xe
int xs,ys; //左端点
int xe,ye; //右端点
int value) //赋给线上的象数值
{
int x; //x以步长为单位从 xs增长到 xe
double dx =xe-xs;
double dy =ye-ys;
double k =dy/dx; // 直线之斜率 k
double y =ys;
for (x=xs; x<=xe; x++) {
WritePixel(x,Round(y),value); //置象数值为 value
y+=k; // y移动步长是斜率 k
} // End of for
} // Line
```