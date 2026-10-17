# 嵌套查询（子查询）

+   - 例：查询选修课程名为“信息系统”的学生学号和姓名-使用连接方法

```
SELECT Sno, Sname
FROM Student, SC, Course
WHERE Student.Sno = SC.Sno  AND
      SC.Cno = Course.Cno AND
      Course.Cname='信息系统';
```