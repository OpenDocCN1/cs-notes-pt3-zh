# 一、 选择表中的若干列

+   1、查询指定列

[例] 查询全体学生的学号与姓名。

```
SELECT Sno, Sname
FROM Student;
```

[例] 查询全体学生的姓名、学号、所在系。

```
SELECT Sname, Sno, Sdept
FROM Student;
```