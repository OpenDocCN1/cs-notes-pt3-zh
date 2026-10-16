# 集合查询（续）

[例] 查询计算机科学系的学生及年龄不大于19岁的学生。

方法一：

```
SELECT *
FROM Student
WHERE Sdept= 'CS'
UNION
SELECT *
FROM Student
WHERE Sage<=19;
```

+   - UNION: 将多个查询结果合并起来时，系统自动去掉重复元组。
+   - UNION ALL: 将多个查询结果合并起来时，保留重复元组

方法二：

```
SELECT DISTINCT *
FROM Student
WHERE Sdept= 'CS' OR Sage<=19;
```