# Bellman-Ford algorithm

E = {(t,x),(t,y),(t,z),(x,t),(y,x),(y,z),(z,x),(z,s),(s,t),(s,y)}

![](bbox=[0.12, 0.35, 0.58, 0.72])

```
BELLMAN-FORD(G, w, s)
1 INITIALIZE-SINGLE-SOURCE(G, s)
2 for i = 1 to |G.V| − 1
3   for each edge (u, v) ∈ G.E
4     RELAX(u, v, w)
5 for each edge (u, v) ∈ G.E
6   if v.d > u.d + w(u, v)
7     return FALSE
8 return
```

![](bbox=[0.28, 0.78, 0.38, 0.9])

![](bbox=[0.7, 0.68, 0.9, 0.85])