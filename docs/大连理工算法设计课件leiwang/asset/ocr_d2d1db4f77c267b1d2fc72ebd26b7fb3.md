# Correctness — Part III (continued)

![](bbox=[0.18, 0.2, 0.82, 0.48])

Since u is the first vertex violating the claimed invariant, we have d[x] = δ(s, x). When x was added to S, the edge (x, y) was relaxed, which implies that d[y] = δ(s, y) ≤ δ(s, u) < d[u]. But, d[u] ≤ d[y] by our choice of u. Contradiction.