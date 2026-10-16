# 数据安全性控制的其它方法（1）

+   - 视图机制
+     - 为不同的用户定义不同的视图，可以将用户对数据访问限制在一定的范围内。
+     - 例：限制王平只能检索Student表中计算机系学生的学号和姓名。
+     Create View CS_Student
+     As Select Sno, Sname From Student
+     Where Sdept = ‘CS’;
+     Grant Select On CS_Student To Wangping;