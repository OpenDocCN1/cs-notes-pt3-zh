# IDENTITY列

+   - 可以设置IDENTITY列的开始值和增量，如
+     CREATE TABLE TEST
+     ( 列1 SMALLINT Identity(-100, 2),
+       列2 VARCHAR(30) NOT NULL)
+     - “列1”的第1条记录的值从-100开始，下一条记录的列1值为上一条的值加2。
+   - 不能人为地向IDENTITY列中插入数值，如，
+     - INSERT INTO 办公室 VALUES (5, ‘就业办公室’, ‘办公楼205’)
+       是错误的。
+   - 但若使用 “SET IDENTITY_INSERT 办公室 ON” 语句，且写出完整的列列表后，就可以在IDENTITY列中插入值，则执行成功:
+     INSERT INTO 办公室( OfficeID, OfficeName, Address)
+     VALUES (5, ‘就业办公室’, ‘办公楼205’)
+   - 再使用 “SET IDENTITY_INSERT 办公室 OFF” 语句恢复不能人为插值的状态