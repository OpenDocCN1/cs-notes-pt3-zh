# 1. 3. 3. 6 SQL中行的分组

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