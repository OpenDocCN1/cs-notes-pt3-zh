# 2.1.4 散列(HASH)簇存储

+   - HASH与聚簇都是把若干有共用列的表聚簇在一起,但聚簇建立专用索引,用索引确定各聚簇键对应行的存储位置;HASH不建索引,通过HASH函数生成HASH值,由HASH值确定键值对应行的存储位置,一步到位。
+   - CREATE CLUSTER clustername ...
+     (colname datatype [,col...]) SIZE n
+     [SINGLE TABLE]HASHKEYS n [HASH IS expr];
+     SINGLE TABLE表示只供一张表优化用。
+     HASHKEYS说明该散列簇至少包含的键数(应该INITIAL的值大于SIZE*HASHKEYS,从而使初始区域放下该散列簇,避免碎片)。

![](bbox=[0.66, 0.38, 0.92, 0.47])