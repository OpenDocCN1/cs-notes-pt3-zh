# 查询视图（续）

[例11]在S_G视图中查询平均成绩在90分以上的学生学号和平均成绩

```
SELECT *
FROM S_G
WHERE Gavg>=90;
```

S_G视图的子查询定义：

```
SELECT Sno, AVG(Grade)
FROM SC
GROUP BY Sno;
```

![](bbox=[0.85, 0.03, 1.0, 0.18])