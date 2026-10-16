# 1. 4. 2. 3 PL/SQL、用户定义函数和方法

+   - 例:对象关系数据库中利用对象类型定义表、利用用户定义函数定义对象的方法。

+   - 1)定义对象点(point_t)和矩形(rectangle_t)及其方法inside(point_t)(点是否在矩形对象内)和area()(矩形面积).

定义点对象

```
create type point_t as object (x int,y int);
```

定义包含方法的矩形对象

```
create type rectangle_t as object (pt1 point_t, pt2 point_t, member function inside(p point_t) return int, member function area return int);
```

成员函数，实际是对象的方法