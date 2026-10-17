# 单表查询

+   - 查询结果分组
+     例：求各个课程号及相应的选课人数。

```
SELECT Cno, COUNT(Sno) FROM SC GROUP BY Cno;
```

例：查询选修了3门以上课程的学生学号。

```
SELECT Sno FROM SC
GROUP BY Sno HAVING COUNT(*) >3;
```