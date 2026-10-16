# SQL Server的数据库备份和恢复

+   - 例：备份“学生-课程数据库”
+     - 创建备份设备
+       ```sql
+       sp_addumpdevice 'disk', 'MyBackup1','c:\Mybackup1.bak'
+       ```
+     - 备份数据库
+       ```sql
+       BACKUP DATABASE StudentCourse TO MyBackup1
+       ```
+     - 创建事务日志备份设备
+       ```sql
+       sp_addumpdevice 'disk', 'MyBackupLog1','c:\MybackupLog1.bak'
+       sp_addumpdevice 'disk', 'MyBackupLog2','c:\MybackupLog2.bak'
+       ```
+     - 备份事务日志1
+       ```sql
+       BACKUP LOG StudentCourse TO MyBackupLog1
+       ```
+     - 备份事务日志2
+       ```sql
+       BACKUP LOG StudentCourse TO MyBackupLog2
+       ```