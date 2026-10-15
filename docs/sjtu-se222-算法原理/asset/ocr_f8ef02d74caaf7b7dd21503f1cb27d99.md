# Basic Ford-Fulkerson

```
**Algorithm 16.1** Ford-Fulkerson  
**Input:** A network \((G, s, t, c)\).  
**Output:** A flow \(f\) in \(G\).  

1. Initialize the residual graph by setting \(R = G\).  
2. for each edge \((u, v) \in E\) do \(f(u, v) \leftarrow 0\)  
3. while there is an augmenting path \(p = s, \ldots, t\) in \(R\) do  
   4. Let \(\Delta\) be the bottleneck capacity of \(p\)  
   5. for each edge \((u, v)\) in \(p\) do \(f(u, v) \leftarrow f(u, v) + \Delta\)  
   6. Update the residual graph \(R\)  
   7. end while
```