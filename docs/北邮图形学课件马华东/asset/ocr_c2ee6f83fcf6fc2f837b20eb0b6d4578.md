# 3) 算法描述

```
Procedure Bresenhamline(xs,ys,xe,ye)
int x, y, deltax, deltay, e;
begin
    deltax:=xe-xs; deltay:=ye-ys;
    e:=-deltax; x:=xs; y:=ys;
    for(i:=0 to deltax) do
    begin
        plot(x, y);
        if (e>=0) then
        begin
            y:=y+1; e:=e-2*deltax;
        end
        x:=x+1; e:=e+2*deltay;
    end
end
```