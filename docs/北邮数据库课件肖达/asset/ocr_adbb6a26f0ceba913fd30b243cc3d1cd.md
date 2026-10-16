# 查询经过计算的值（续）

[例] 查询全体学生的姓名、出生年份和所有系，要求用小写字母表示所有系名

```
SELECT Sname,  ‘Year of Birth:’,  2007-Sage,
       LOWER(Sdept)
FROM Student;
```

# 输出结果：

| Sname | 'Year of Birth:' | 2007-Sage | LOWER(Sdept) |
|---|---|---:|---|
| 李勇 | Year of Birth: | 1987 | cs |
| 刘晨 | Year of Birth: | 1988 | is |
| 王敏 | Year of Birth: | 1989 | ma |
| 张立 | Year of Birth: | 1988 | is |