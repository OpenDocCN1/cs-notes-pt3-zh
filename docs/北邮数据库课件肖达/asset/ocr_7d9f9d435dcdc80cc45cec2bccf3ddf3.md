# 删除基本表（续）

[例12]如果选择CASCADE时可以删除表，视图也自动被删除

```
DROP TABLE Student CASCADE;
```

--NOTICE: drop cascades to view IS_Student

```
SELECT * FROM IS_Student;
```

--ERROR: relation " IS_Student " does not exist