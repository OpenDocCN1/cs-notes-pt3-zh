# # 1) David F. Rogers 描述描述

```
// Select the larger of Δx or Δy to be one raster unit.
StepX = ( xe -xs) / Length;
StepY = ( ye -ys) / Length;
x = xs; //首点
y = ys;
i = 1; // Begin main loop
while (i≤ Length)
    WritePixel (Round(x), Round(y) ,value));
    x = x + StepX;
    y = y + StepY;
    i++;
end while
```