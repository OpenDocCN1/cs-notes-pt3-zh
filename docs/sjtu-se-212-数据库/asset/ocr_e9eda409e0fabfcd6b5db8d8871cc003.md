# DML: Query, Aggregation

统计软件学院男女生平均年龄及人数

```
SELECT gende, AVG(age), COUNT(*)
FROM student
WHERE dept = 'SE'
GROUP BY dept, gende
```