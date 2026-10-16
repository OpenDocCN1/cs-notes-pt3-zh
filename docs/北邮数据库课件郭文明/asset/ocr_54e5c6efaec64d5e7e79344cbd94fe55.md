# 1. 3. 3. 6 SQL中行的分组

+   - 如果要去掉分组后的某些行，不能用where，只能用HAVING子句。
+     例:求被至少两个顾客订购的产品pid.
+     select pid from orders
+     group by pid having count(distinct cid) >=2;
+   - 如果没有GROUP BY只有HAVING，则整个结果为一组.
+   - 基本SQL select语句的通用形式不允许集合函数的嵌套.但可以有变通的GROUP BY形式.
+     例:求所有代理商的最大销售额的平均值.