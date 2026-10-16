# 1.3.3.3 UNION运算和FOR ALL条件

![](bbox=[0.02, 0.25, 0.08, 0.38])

SQL中没有等价的÷运算。如果面临的查询“要求被检索的对象集合必须符合‘所有’这类关键词的条件”(FOR ALL)时，关系代数要用除运算。SQL中可以：

+   1. 表述要检索的候选对象的一个反例(至少一个对象不符合条件)，. 并建立select语句(选出所有反例)； 2. 建立表示这类反例不存在的条件(not exists)； 3. 建立最终select。

例：求通过住在北京的所有代理商订了货的顾客cid.

+   1. 反例：住在北京但没有为所求顾客c.cid订货的代理商：

```
select * from agents where a.city='北京'  and not exists
(select * from orders x where x.cid=c.cid and x.aid=a.aid)
```

+   2. 反例不存在： not exists (反例)

+   3. 最终： select c.cid from customers where  not exists

```
(select * from agents where a.city='北京'  and not exists
(select * from orders x where x.cid=c.cid and x.aid=a.aid));
```