# # Subproblems identification by intermediate vertices

+   - Define \( d_{ij}^m = \) weight of a shortest path from i to j that only uses intermediate vertices from set \(\{1, \dots, m\}\) or
+   - Define \( d_{ij}^m = \) weight of a shortest path from i to j that the orders of intermediate vertices is no larger than m
+   - \( d_{ij}^n \) is our goal
+   - We have known that
+     - \( d_{ij}^0 = a_{ij} \)
+     - \( d_{ik}^{k-1} = d_{ik}^k \)