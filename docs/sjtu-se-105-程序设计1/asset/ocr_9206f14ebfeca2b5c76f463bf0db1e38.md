# 定义

+   - 完整指定所声明实体的声明被称为定义
+     - 例如
+       int a = 7;
+       int b; // an int with the default value (0)
+       vector<double> v; // an empty vector of doubles
+       double sqrt(double) { ... }; // i.e. a function with a body
+       struct Point { int x; int y; };
+     - 不是定义的声明
+       double sqrt(double); // function body missing
+       struct Point; // class members specified elsewhere
+       extern int a; // extern means “not definition”
+       // “extern” is archaic; we will hardly use it