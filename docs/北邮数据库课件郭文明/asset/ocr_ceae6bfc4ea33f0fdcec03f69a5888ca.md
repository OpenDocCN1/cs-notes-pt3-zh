# 1. 4. 2. 3 PL/SQL、用户定义函数和方法

+   • 3) 使用方法area和inside.

计算rects表中矩形面积：

```
select value(x),x.area() from rects x;
```

判断点(4,2)是否在每个矩形中：

```
select value(x),x.inside(point_t(4,2)) from rects x;
```

查询在所有矩形内的所有点：

```
select value(p) from points p where not exists
(select * from rects r where r.inside(p)=0);
```

计算覆盖各点的最小矩形的面积：

```
select p.x,p.y,min(r.area()) from rects r,points p
where r.inside(value(p))>0 group by p.x,p.y;
```

将面积小于24的矩形的pt2横纵坐标加1：

```
update rects r set pt2=point_t(r.pt2.x+1,r.pt2.y+1) where r.area()<24;
```