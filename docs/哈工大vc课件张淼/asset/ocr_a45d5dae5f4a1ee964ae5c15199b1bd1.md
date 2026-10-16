# # new和malloc比较

+   - 程序执行效率
+     - new和delete是运算符，执行效率高
+     - malloc和free是函数，执行效率相对较低

+   - 其他
+     - 如果创建的是动态对象，new会去调用对象类的构造函数，而malloc则不会