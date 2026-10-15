# Dijkstra 3-way partitioning

+   - Let v be partitioning item a[lo].
+   - Scan i from left to right.
+     - (a[i] < v): exchange a[lt] with a[i] and increment both lt and i
+     - (a[i] > v): exchange a[gt] with a[i] and decrement gt
+     - (a[i] == v): increment i

![](bbox=[0.14, 0.52, 0.88, 0.68])

![](bbox=[0.33, 0.73, 0.78, 0.92])