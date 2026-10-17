# SQL数据定义语言

+   - 修改基本表-删除完整性约束

```
ALTER TABLE table_name
DROP constraint;
```

+   - 例：
+     删除学生姓名必须取唯一值的约束。

```
ALTER TABLE student
DROP unique(sname);
```