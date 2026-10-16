# 4.1 数组

➤ 复合类型数组使用运算符new为只是为数组本身分配空间，并没有对数组的元素进行初始化。对于复合类型的数组，需要经过两步进行空间分配：

+   ✓ 创建数组本身：
+    type arrayName[]=new type[arraySize];

+   ✓ 创建各个数组元素：
+    arrayName[0]=new type(paramList);
+    arrayName[1]=new type(paramList);
+    ......
+    arrayName[arraySize-1]=new type(paramList);