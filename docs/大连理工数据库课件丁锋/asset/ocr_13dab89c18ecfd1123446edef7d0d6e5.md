# # SQL数据定义语言

+   - 修改基本表-改变列的数据类型

```
```sql
ALTER TABLE table_name
ALTER COLUMN column_name new_datatype;
```
```

+   - 例：
+     将年龄的数据类型改为半字长整数。

```
```sql
ALTER TABLE Student
ALTER COLUMN Sage SMALLINT;
```
```