# 1.3.3.2 子查询

+   3) EXISTS谓词: EXISTS (Subquery)为真当且仅当子查询返回一个非空集合；NOT EXISTS (Subquery)为真当且仅当返回集合为空。

例:求出既订购了产品p01有订购了产品p07的顾客cid.

关系代数: π_cid(σ_pid='p01'(O)) ∩ π_cid(σ_pid='p07'(O))

```
select distinct cid from orders x where pid='p01' and exists (select * from orders where cid=x.cid and pid='p07');
```

或 select distinct x.cid from orders x,orders y where x.pid='p01' and x.cid=y.cid and y.cid='p07';

EXISTS的查询一般能找到等价的其他查询形式。

交运算

使用和不使用exists