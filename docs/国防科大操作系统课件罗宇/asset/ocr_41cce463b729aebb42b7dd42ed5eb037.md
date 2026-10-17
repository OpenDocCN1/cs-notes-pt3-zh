# 巨星陨落

```
```
for v in Vertices (0): 
d[v] = Infinity
T.Add(s)
while T.IsNotEmpty():
v = pickMinimal(T, d)
T.Remove(v)
for v in Neighborhood(v):
if d[v] > d[v] + weight[v,v]
d[v] = d[v] + weight[v,v]
pred[v] = v
```
```

![](bbox=[0.52, 0.15, 0.98, 0.58])

+   - 加权有向图的最短路径问题
+   - 经典，完美的 Dijkstra算法
+   - 应用无处不在