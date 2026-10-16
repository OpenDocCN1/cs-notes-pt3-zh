# 3.1.6 嵌入式SQL语句

+   - **检索**: EXEC SQL SELECT [ALL|DISTINCT] 表达式 INTO 宿主变量 FROM 表名 WHERE 条件;
+   - **游标定义**: EXEC SQL DECLEARE 游标名 CURSOR FOR 子查询 [ORDER BY...] [FOR READ ONLY | UPDATE [OF 列名]];
+   - **游标打开与关闭**: EXEC SQL OPEN|CLOSE 游标名;
+   - **游标取值**: EXEC SQL FETCH [NEXT|PRIOR|FIRST|LAST |CURRENT|RELETIVE n|ABSOLUTE n] 游标名 INTO 宿主变量;
+   - **删除**: EXEC SQL DELETE FROM 表名 [WHERE条件 | WHERE CURRENT OF 游标名];
+   - **修改**: EXEC SQL UPDATE 表名 SET 列=表达式 [WHERE 条件|WHERE CURRENT OF 游标名];
+   - **增加**: EXEC SQL INSERT INTO 表名 [(列名)] VALUES(表达式);