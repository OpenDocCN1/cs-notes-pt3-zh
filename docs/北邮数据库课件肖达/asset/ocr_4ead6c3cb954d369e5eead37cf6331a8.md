# IDENTITY列

+   - 使用IDENTITY列
+     - 列的属性除NULL和NOT NULL外，还可以使用IDENTITY特性
+     - 标识为IDENTITY的列不必在插入行时为其赋值，系统会自动添加唯一的行序号
+     - 每个表中有且仅有一个IDENTITY列，该列不允许为空，不允许设置默认值