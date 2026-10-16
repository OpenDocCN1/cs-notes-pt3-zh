
## 1.3.3.4 高级SQL语法

+   • 2) 连接形式

通用形式： FROM tablename [[AS] corr_name [,......].....]

SQL-99： FROM后面还可以是：

一般形式：

```
tablename[[AS] corr_name[(colname[,colname......])]]
```

子查询：

```
(subquery) [AS] corr_name[(colname[,colname......])]
```

显式连接：

```
table1 [INNER|{LEFT|RIGHT|FULL}[OUTER]] JOIN table2
ON condition
```

显然SQL-99中允许子查询出现在FROM子句中。以上三种形式在产品中并没有完全实现。使用时可以试用或帮助。

例：检索至少订购了一件价格低于0.5的商品的顾客姓名。

```
select distinct cname from
(orders o join products p on o.pid=p.pid)
join customers c on o.cid=c.cid
where p.price<0.5;
```

注：ORACLE仅提供左连和右连，而且语法与标准SQL也不同：

```
SELECT ... FROM T1,T2
WHERE [T1.c1[(+)]=T2.c2 | T1.c1=T2.c2[(+)] ] AND condition
```

T2保留所有行

与T1连不上的用NULL

## 1.3.3.5 SQL中的集合函数

+   SQL中称集合函数(set function), ORACLE称组函数(group function), DB2 UDB称列函数(column function), INFORMIX称聚集函数(aggregate function).

| 名称 | 参数类型 | 结果类型 | 描述 |
|---|---|---|---|
| COUNT | 任意(*) | 数值 | 出现次数 |
| SUM | 数值 | 数值 | 参数和 |
| AVG | 数值 | 数值 | 参数均值 |
| MAX | 字符,数值 | 字符,数值 | 最大值 |
| MIN | 字符,数值 | 字符,数值 | 最小值 |

+   集合函数语法: SET_FUNCTION ([ALL|DISTINCT] col) | COUNT(*)
+   注: ALL时包括重复行，DISTINCT不包括重复行。
+   WHERE子句比较操作中不能使用集合函数. 如discnt<max(...)
+   集合函数忽略了所有空值.
+   集合函数不允许嵌套使用. 如AVG(select MAX(dollars)......)

## 1.3.3.6 SQL中行的分组

+   - SQL报表功能: 根据某些列值的共性把一个表所包含的全部行分成若干个子集, 然后对每个子集执行集合函数.

例: 打印每个代理商为顾客c002和c003订购产品及产品总数.

```
select a.aid, aname, p.pid, pname, sum(qty)
from orders x, products p, agents a
where x.pid=p.pid and x.aid=a.aid
    and x.cid in ( 'c002' , ' c003' )
group by a.aid, a.aname, p.pid, p.pname;
```

+   - GROUP BY对象的列上的空值会被分在同一组里.

+   - 如果要去掉分组后的某些行，不能用where，只能用HAVING子句。
+     例:求被至少两个顾客订购的产品pid.
+     select pid from orders
+     group by pid having count(distinct cid) >=2;
+   - 如果没有GROUP BY只有HAVING，则整个结果为一组.
+   - 基本SQL select语句的通用形式不允许集合函数的嵌套.但可以有变通的GROUP BY形式.
+     例:求所有代理商的最大销售额的平均值.

+   - 例:求所有代理商的最大销售额的平均值.

错： select avg(select max(dollars) from orders group by aid);

对： SQL高级形式,ORACLE中可行：

```
select avg(t.x) from (select aid,max(dollars) as x from orders group by aid) t;
```

常用作法：

```
creat view t as (select aid,max(dollars) as x from orders group by aid);
```

```
select avg(t.x) from t;
```

## 1.3.4 SQL数据更新

+   - SQL中数据更新包括插入数据 (Insert)、修改数据 (Update) 和删除数据 (Delete) 三条语句。

+   - 1.3.4.1 插入数据
+     INSERT INTO <表名>[ (<属性列1>[, <属性列2>...])]
+     [VALUES (expr1 | NULL [, expr2 | NULL]...) | Subquery]
+     将新元组插入指定表中，其中新记录属性列1的值为expr1，属性列2的值为expr2。...。INTO子句中没有出现的属性列，新记录在这些列上将取空值。还可通过子查询批量插入数据。

+   - 在表定义时说明了 NOT NULL 的属性列不能取空值，否则会出错。

+   如果 INTO 子句中没有指明任何列名，则新插入的记录必须在每个属性列上均有值，给定值对应于表定义的字段顺序。

+   子查询不需要用括号括起来。

```
insert into my_c select * from customers where city='北京';
```

```
insert into my_c (select * from customers where city='北京');
```

![](img/ffd1e1f008d7fcbd0b52f1e6bcb7a952_113_0.png)

![](img/ffd1e1f008d7fcbd0b52f1e6bcb7a952_113_1.png)

### 1.3.4.1 修改数据

```
UPDATE <表名>
SET <列名1>=<expr1|NULL|(Subquery)>
[, <列名2>=<expr2|NULL|(Subquery)>...]
[WHERE <条件>];
```

+   - 其功能是修改指定表中满足WHERE子句条件的元组。其中SET子句给出expr的值用于取代相应的属性列值。如果省略WHERE子句，则表示要修改表中的所有元组。

+   - 只有一个表可以作为UPDATE的对象。有些系统中不允许在SET子句中使用限定属性名。

```
update agents set agents.percent=1.1*agents.percent
```

+   - Entry SQL-92中SET子句中不能用子查询，但SQL-99及ORACLE、DB2、UDB等都支持。

用customers表中最新discnt更新my_c中discnt

```
update my_c set discnt=(select discnt from customers where cid=my_c.cid)
```

+   - 删除语句的一般格式为：
+     DELETE FROM <表名> [WHERE <条件>]
+     从指定表中删除满足WHERE子句条件的所有元组。如果省略WHERE子句，表示删除表中全部元组，但表的定义仍在字典中。DELETE语句删除的是表中的数据，而不是关于表的定义。

+   - 删除条件中可以有子查询
+     删除总订货金额小于600的代理商：
+     delete from agents where aid in (select aid from orders group by aid having sum(dollars)<600);

+   - 增删改操作只能对一个表操作。因此在执行增删改操作时,要注意数据库中数据的一致性。

## 作业：

+   1. 检索佣金百分率大于最小百分率的代理商aid.
+   2. 求通过住在北京或上海的代理商订货的顾客cid. (使用子查询和不使用子查询两种)
+   3. R、S和T具有相同的属性列A1......An, 不用高级SQL来实现关系表达式(R UNION S) MINUS T.
+   4. 求出没有为任何住在北京的顾客订购任何在天津生产的产品 的代理商的aid.
+   5. 没有一个包含GROUP BY子句的查询会返回重复行，这一命题为真吗?如果为真, 解释原因; 否则, 给出反例.
+   6. 说出你所用到DBMS和其中的SQL语句, 他们与讲课时的不一样或者不能用.
