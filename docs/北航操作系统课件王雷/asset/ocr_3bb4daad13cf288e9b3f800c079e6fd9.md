# 存取控制的实现方案

+   - 存取控制矩阵
+   - 存取控制表
+   - 用户权限表
+   - 口令

Mode of access: read, write, execute
Three classes of users

a) owner access
RWX
7 ⇒ 1 1 1
b) group access
RWX
6 ⇒ 1 1 0
c) public access
RWX
1 ⇒ 0 0 1

![](bbox=[0.44, 0.045, 0.93, 0.64])