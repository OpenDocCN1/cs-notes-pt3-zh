# 1.3.4 SQL数据更新

+   如果 INTO 子句中没有指明任何列名，则新插入的记录必须在每个属性列上均有值，给定值对应于表定义的字段顺序。

+   子查询不需要用括号括起来。

```
insert into my_c select * from customers where city='北京';
```

```
insert into my_c (select * from customers where city='北京');
```

![](bbox=[0.62, 0.29, 0.89, 0.37])

![](bbox=[0.62, 0.6, 0.71, 0.68])

# 1.3.4.1 修改数据

```
UPDATE <表名>
SET <列名1>=<expr1|NULL|(Subquery)>
[, <列名2>=<expr2|NULL|(Subquery)>...]
[WHERE <条件>];
```