# 7.10 多粒度锁 Lock Granularities

多级锁：从减少lock开销来讲，锁定单位越大越好；从提高事务运行并发度来讲，粒度越小越好。

所以大数据库中锁定单位分几级：

DB—File—Record—Field

In this situation, if a transaction acquires a lock on a node then it acquires implicitly the same lock on each descendant of that node.