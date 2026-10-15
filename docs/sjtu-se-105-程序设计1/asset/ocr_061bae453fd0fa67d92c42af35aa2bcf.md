# 如何定义MaxIntSet

+   - 私有意味着它们只对这个类的其他成员是可见的
+   - IntSet中的所有数据成员对于下列成员是不可访问的
+     - MaxIntSet类的成员实现
+     - 特别是MaxIntSet::max()
+   - max()不是IntSet的一部分
+     - 它只是MaxIntSet的一部分