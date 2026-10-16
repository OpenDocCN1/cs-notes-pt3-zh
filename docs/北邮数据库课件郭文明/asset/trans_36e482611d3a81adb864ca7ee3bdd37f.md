

# 1. 4. 2. 1 ORACLE中对象类型

+   - 可用嵌套的点号访问一个对象的属性, 无名顶层列可以用 VALUE() 形式引用行对象.

```
select * from employees e where e.job='经理' ;
```

| eid | ename(name,sex) | job |
| 0001 | namesex_t('赵子龙','男') | 经理 |

```
select value(e) from employees e where e.job='经理' ;
```

| value(e) | (eid  ename(name,sex)  job) |
| employee_t (0001 namesex_t('赵子龙','男') 经理) | |

```
select e.eid,e.job from employees e
where e.ename=namesex_t('孟可飞','女') ;
```

# 1. 4. 2. 1 ORACLE中对象类型

+   一个对象类型不能嵌套包含与自己类型相同的成分(递归),但可以包含对同样类型的引用。

建一个配偶对象表：

```
create type mate_t as object
(mid char(4),mname namesex_t, partner ref mate_t);
create table mates of mate_t
(primary key (mid), scope for (partner) is mates);
```

检索其配偶为女性的人名：

```
select mname.name from mates m where m.partner.mname.sex='女';
```

+   一个表集合可以具有一个用ref表示的复杂关系集.如雇员有部门,部门有经理,经理又是雇员.回路的依赖中删除时用DROP TYPE ... FORCE.

# 1. 4. 2. 2 ORACLE集合类型

+   - ORACLE有两种集合类型:表类型和数组类型.集合类型是数据库成熟的数据类型,经过适当的转换,可以在查询中解释为表。

+   - 表类型和嵌套表创建：表类型名
+   CREATE TYPE typename AS TABLE OF obj_name;
+   CREATE TABLE tablename
+   ( 属性名 类型[NOT NULL][...] )
+   [NESTED TABLE 属性名 STORE AS tablename]
+   [,NESTED TABLE 属性名 STORE AS tablename...];

已建的对象

父表

子表

表类型的属性

# 1. 4. 2. 2 ORACLE汇集类型

+   例：

```
create type depe_t as table of namesex_t;
create table employees
(eid char(4),ename namesex_t,dependents depe_t,
primary key (eid) )
nested table dependents store as d_tab;
```

| eid | ename | Dependents |
|---|---|---|
| 0001 | namesex_t('张家口','男') | namesex_t('李小玫','女') |
|  |  | namesex_t('张冠李','男') |
| 0002 | namesex_t('柴米油','男') | namesex_t('陆续琴','女') |
| 0003 | namesex_t('郝成功','男') | namesex_t('朱那亚','女') |
|  |  | namesex_t('郝乃军','男') |
|  |  | namesex_t('郝佳欣','女') |

# 1. 4. 2. 2 ORACLE汇集类型

+   - 子表的数据只能通过父表来访问。

检索0001号职工的家属：

对象列必须加限定非对象列不加

```
select dependents from employees where eid='0001';
```

检索有2个家属以上的职工eid：

```
select eid from employees e where 2<(select count(*) from table(e.dependents));
```

Table()将e.dependents转换为一表

检索0003号职工的家属数目：

错误:select count(*) from (select e.dependents from employees e where e.eid='0003');

错误:select count(*) from (select table(e.dependents) from employees e where e.eid='0003');

正确:select count(*) from table (select e.dependents from employees e where e.eid='0003');

# 1. 4. 2. 2 ORACLE集合类型

+   - 利用表的乘积可以消除表的嵌套。

显示职工号及其家属名：

```
select e.eid,d.name from employees e,
    table(e.dependents) d;
```

没有家属的eid不显示

```
select e.eid,d.name from employees e,
    table(e.dependents) (+) d;
```

(+)表示外连，没有家属的eid也显示

显示具有最大家属名的职工号及其家属名：

```
select e.eid,d1.name from employees e,
    table(e.dependents) d1 where d1.name=
    (select max(d2.name)
        from table(e.dependents) d2);
```

# 1.4.2.2 ORACLE汇集类型

+   - ORACLE的另一种汇集类型即数组类型,以 VARRAY声明。

```
create type phone_t as varray(4) of int;
create table employees
  (eid char(4),ename namesex_t,
   telephone phone_t, primary key (eid)) ;
```

| eid | ename | telephone |
|---|---|---|
| 0001 | namesex_t('张家口','男') | phone_t(12345678,23456789) |
| 0002 | namesex_t('柴米油','男') | phone_t(34567890) |
| 0003 | namesex_t('郝成功','男') | phone_t(45678901,56789012,67890123) |

# 1. 4. 2. 2 ORACLE集合类型

+   - SQL语句不能访问数组的下标. 在嵌入主语言后, 从一行检索的数组可付给编程语言的数组.
+   TABLE() 可以应用于VARRAY.
+   例:列出电话号码为45678901的人:
+   select eid,ename from employees e where 45678901 in (select * from table(e.telephone));

+   - 集合类型(表类型和数组)的更新用集合构造器.
+   Insert into employees values ('0006',namesex_t('孙子兵','男'), phone_t(68888888,96666666));
+   Update employees set telephone=phone_t(80166666,80166667) where eid='0001';

![](img/ffd1e1f008d7fcbd0b52f1e6bcb7a952_141_0.png)

# 1.4.2.3 PL/SQL、用户定义函数和方法

+   • 非过程的SQL不具备计算的完整性。ORACLE引入PL/SQL，INFORMIX引入SPL，SQLSERVER引入T-SQL。
过程SQL支持内存驻留变量、条件和循环结构、过程和函数等。

+   • 一个用过程SQL编写的函数在服务器上执行时被称为存储过程，由Create Function语句记录在服务器上的数据库目录表中。

+   • 触发器是可以在任意事件发生时执行的过程性SQL语句块。触发器用于实现定制的约束或缺省行为。

+   • 用户定义函数(UDF)是用过程性SQL(或C、Java)写的函数，可以像交互式SQL中的内部函数一样被调用。

+   • 方法是与用户定义类型一起定义的用户定义函数。

