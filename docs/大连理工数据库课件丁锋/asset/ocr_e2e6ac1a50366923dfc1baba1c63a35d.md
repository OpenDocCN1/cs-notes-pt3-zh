# 单表查询

+   - 消除取值重复的行

例：查询选修了课程的学生学号。

```
SELECT DISTINCT Sno FROM SC;
```

例：查询选修课程的各种成绩

```
SELECT DISTINCT Cno, Grade FROM SC;
```

> > 注意：DISTINCT短语的作用范围是所有目标列