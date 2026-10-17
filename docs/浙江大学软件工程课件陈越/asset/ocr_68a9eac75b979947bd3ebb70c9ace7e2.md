# § 2.模块化原理

◆ 公共耦合（Common coupling）：Data are accessible from a common data store.

![](bbox=[0.073, 0.221, 0.935, 0.745])

问题：

+   - 公共部分的改动将影响所有调用它的模块；
+   - 公共部分的数据存取无法控制；
+   - 复杂程度随耦合模块的个数增加而增加。