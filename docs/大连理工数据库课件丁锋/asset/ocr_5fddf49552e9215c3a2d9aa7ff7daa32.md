# SQL数据定义语言

+   练习
+   创建一个课程表

建立一个“课程”表Course，它由课程号Cno、课程名Cname、先行课Cpno、学分Ccredit四个属性组成。其中课程号不能为空，值是唯一的，并且课程名取值也唯一。

```
CREATE TABLE
Course(
Cno CHAR(9) NOT NULL UNIQUE,
Cname CHAR(20) UNIQUE,
Cpno CHAR(2),
Credit NUMERIC(2,0)
);
```