# Interval search tree

Search (lo, hi):

+   - If interval in node intersects query interval, return it.
+   - If left subtree is null, go right.
+   - If max endpoint in left subtree is less than lo, go right.
+   - Else go left.

interval intersection
search for (23, 25)
(12, 14)
(21, 23)

![](bbox=[0.28, 0.45, 0.88, 0.95])