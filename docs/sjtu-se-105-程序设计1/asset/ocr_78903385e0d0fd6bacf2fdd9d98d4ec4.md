# 类的优点

+   - 聚集的优点
+     `void add_one (int a[], int elts);`
+     - 丑陋!
+     - 危险： elts值有误怎么办?
+     `void add_one (IntSet& set);`
+     - 计数值和数组不再分离
+     - 隐藏了集的表示