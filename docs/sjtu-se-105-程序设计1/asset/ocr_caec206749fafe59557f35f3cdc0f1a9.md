# 构造函数重载

+   - 重载的构造函数将创建一个具有指定尺寸的数组：
+     `IntSet::IntSet(int size)`
+     ```
+     {
+       elts = new int[size];
+       sizeElts = size;
+       numElts = 0;
+     }
+     ```
+   - 这属于函数重载