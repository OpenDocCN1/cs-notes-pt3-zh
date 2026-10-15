# Quicksort partitioning

Repeat until i and j pointers cross.

+   - Scan i from left to right so long as a[i] < a[lo].
+   - Scan j from right to left so long as a[j] > a[lo].
+   - Exchange a[i] with a[j].

![](bbox=[0.11, 0.66, 0.89, 0.82])

stop i scan because a[i] >= a[lo]