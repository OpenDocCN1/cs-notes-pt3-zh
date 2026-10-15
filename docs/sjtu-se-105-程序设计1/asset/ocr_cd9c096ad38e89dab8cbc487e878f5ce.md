# 抽象类

+   - 具体实现可以由导出类提供：
+     ```
+     const int MAXELTS = 100;
+     class IntSetImpl : public IntSet {
+         int elts[MAXELTS];
+         int numElts;
+     public:
+         IntSetImpl();
+         void insert(int v);
+         void remove(int v);
+         bool query(int v);
+         int size();
+     };
+     ```