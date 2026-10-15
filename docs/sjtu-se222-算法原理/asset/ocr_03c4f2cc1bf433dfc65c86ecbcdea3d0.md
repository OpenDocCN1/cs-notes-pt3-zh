# The problem

Problem: DynamicConnectivity
Input: n sites, m operations (union or connected query)
Output: the answer of connected queries

```
union(4, 3)
union(3, 8)
union(6, 5)
union(9, 4)
union(2, 1)
connected(0, 7)  X
connected(8, 9)  ✓
union(5, 0)
union(7, 2)
union(6, 1)
connected(0, 7)  ✓
union(1, 0)
```

![](bbox=[0.38, 0.48, 0.92, 0.72])