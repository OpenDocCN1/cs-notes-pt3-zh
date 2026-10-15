+   - 有了 indexOf， query 就容易编写了：
+     ```
+     bool IntSet::query(int v)
+     {
+       return (indexOf(v) != MAXELTS);
+     }
+     ```
+   - insert 也不会困难多少：
+     - 首先查找待插入元素的索引
+     - 如果不存在，则需要插入该元素
+     - 插入的方式是在数组末尾添加