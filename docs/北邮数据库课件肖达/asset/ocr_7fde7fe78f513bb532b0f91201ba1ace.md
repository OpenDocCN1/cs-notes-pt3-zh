# 修改数据（续）

[例5] 将学生200215121的年龄改为22岁

```
UPDATE Student
SET Sage=22
WHERE Sno='200215121';
```

[例6] 将所有学生的年龄增加1岁

```
UPDATE Student
SET Sage= Sage+1;
```

[例7] 将计算机科学系全体学生的成绩置零。

```
UPDATE SC
SET Grade=0
WHERE 'CS'=
(SELECT Sdept
FROM Student
WHERE Student.Sno = SC.Sno);
```