# # Correctness — Part III

**Theorem.** Dijkstra’s algorithm terminates with $d[v] = \delta(s, v)$ for all $v \in V$.

*Proof:* It suffices to show that $d[v] = \delta(s, v)$ for every $v \in V$ when $v$ is added to $S$. Suppose $u$ is the first vertex added to $S$ for which $d[u] > \delta(s, u)$. Let $v$ be the first vertex in $V-S$ along a shortest path from $s$ to $u$, and let $x$ be its predecessor:

![](bbox=[0.079, 0.637, 0.93, 0.906])