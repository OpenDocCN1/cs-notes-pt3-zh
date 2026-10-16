# 建立视图（续）

# 分组视图

[例6] 将学生的学号及他的平均成绩定义为一个视图
假设SC表中“成绩”列Grade为数字型

```
CREAT VIEW S_G(Sno, Gavg)
AS
SELECT Sno, AVG(Grade)
FROM SC
GROUP BY Sno;
```