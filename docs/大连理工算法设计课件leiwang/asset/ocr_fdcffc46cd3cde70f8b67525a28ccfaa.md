# # Correctness

**Theorem.** If $G=(V,E)$ contains no negative-weight cycles, then after the Bellman-Ford algorithm executes, $d[v]=\delta(s,v)$ for all $v\in V$.

*Proof.* Let $v\in V$ be any vertex, and consider a shortest path $p$ from $s$ to $v$ with the minimum number of edges.

![](bbox=[0.067, 0.529, 0.929, 0.746])

Since $p$ is a shortest path, we have

$\delta(s,v_i)=\delta(s,v_{i-1})+w(v_{i-1},v_i)$.