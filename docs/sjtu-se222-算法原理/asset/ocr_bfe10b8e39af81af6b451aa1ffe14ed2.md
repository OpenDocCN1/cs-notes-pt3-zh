# Quicksort partitioning

Repeat until i and j pointers cross.

+   - Scan i from left to right so long as a[i] < a[lo].
+   - Scan j from right to left so long as a[j] > a[lo].
+   - Exchange a[i] with a[j].

When pointers cross.

+   - Exchange a[lo] with a[j].

![](bbox=[0.12, 0.62, 0.88, 0.8])

pointers cross: exchange a[lo] with a[j]