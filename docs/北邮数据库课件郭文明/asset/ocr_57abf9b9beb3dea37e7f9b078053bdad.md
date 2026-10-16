# 1. 4. 2. 2 ORACLE集合类型

+   - SQL语句不能访问数组的下标. 在嵌入主语言后, 从一行检索的数组可付给编程语言的数组.
+   TABLE() 可以应用于VARRAY.
+   例:列出电话号码为45678901的人:
+   select eid,ename from employees e where 45678901 in (select * from table(e.telephone));

+   - 集合类型(表类型和数组)的更新用集合构造器.
+   Insert into employees values ('0006',namesex_t('孙子兵','男'), phone_t(68888888,96666666));
+   Update employees set telephone=phone_t(80166666,80166667) where eid='0001';

![](bbox=[0.7, 0.62, 0.88, 0.7])