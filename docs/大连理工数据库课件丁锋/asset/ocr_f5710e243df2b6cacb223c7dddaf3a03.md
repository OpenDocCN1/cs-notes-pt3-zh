# # 视图

+   - 分组视图

例: 将学生的学号及其的平均成绩定义为一个视图

```
```sql
CREATE VIEW S_G(Sno, Gavg)
AS
SELECT Sno, AVG(Grade)
FROM SC GROUP BY Sno;
```
```