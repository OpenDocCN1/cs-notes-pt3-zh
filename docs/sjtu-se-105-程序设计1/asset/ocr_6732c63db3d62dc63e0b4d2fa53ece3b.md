# 如何定义MaxIntSet

+   - 必须实现MaxIntSet::max()
+   - 但是，MaxIntSet::max()不是IntSet的成员
+   - IntSet的定义如下：
+     ```
+     class IntSet  // OVERVIEW: a mutable set of integers
+     public:
+         void insert(int v);  // MODIFIES: this
+                             // EFFECTS: this = this + {v}
+         void remove(int v); // MODIFIES: this
+                             // EFFECTS: this = this - {v}
+         bool query(int v);   // EFFECTS: returns true if v is in this
+         int size();          // EFFECTS: returns |this|
+     ;
+     ```
+   - IntSet的所有数据成员都是私有的